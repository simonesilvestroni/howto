# How to create a local SSL

## Becoming a (tiny) Certificate Authority

When you generate a self-signed certificate the browser doesn’t trust it. It’s self-signed. It hasn’t been signed by a CA. But we can generate our own root certificate and private key, add the root certificate to all the devices we own just once, and then all certificates that we generate and sign will be inherently trusted.

First, we generate our private key:

```bash
openssl genrsa -des3 -out m2mCA.key 2048
```

You will be prompted for a passphrase. The pass phrase will prevent anyone who gets your private key from generating a root certificate of their own. Then we generate a root certificate:

```bash
openssl req -x509 -new -nodes -key m2mCA.key -sha256 -days 1825 -out m2mCA.pem
```

You will prompted for the passphrase of your private key (that you just chose) and a bunch of
questions. The answers to those questions aren’t that important. They show up when looking at the certificate, which you will almost never do. I suggest *m* *aking the Common Name something that you’ll recognize as your root certificate in a list of other certificates*. That’s really the only thing that matters.

You should now have two files:

1. m2mCA.key (your private key)
2. m2mCA.pem (your root certificate)

## **Installing Your Root Certificate**

We need to add the root certificate to any laptops, desktops, tablets, and phones that will be
accessing your HTTPS sites. This can be a bit of a pain, but the good news is that we only have to do
it once. Once our root certificate is on each device, it will be good until it expires.

Adding the Root Certificate to macOS Keychain

- Open the macOS Keychain app
- Go to File > Import Items...
- Select your private key file (i.e. m2mCA.pem)
- Search for whatever you answered as the Common Name name above
- Double click on your root certificate in the list
- Expand the Trust section
- Change the When using this certificate: select box to “Always Trust”
- Close the certificate window
- It will ask you to enter your password

## **Creating CA-Signed Certificates for Your Dev Sites**

Now that we’re a CA on all our devices, we can sign certificates for any new dev sites that need
HTTPS. First, we create a private key:

```bash
sudo openssl genrsa -out local.minutestomidnight.co.uk.key 2048
```

Then we create a CSR:

```bash
sudo openssl req -new -key local.minutestomidnight.co.uk.key -out local.minutestomidnight.co.uk.csr
```

You’ll get all the same questions as you did above. In this case, the answers don’t matter, because you won’t be looking at this certificate in a list next to others.

Next we’ll create the certificate using our CSR, the CA private key, the CA certificate, and a config file, but first we need to create that config file. The config file is needed to define the Subject Alternative Name (SAN) extension. I created a new file named **minutestomidnight.ext** and added the following contents:

```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = [alt_names]
DNS.1 = local.minutestomidnight.co.uk
```

Now we run the command to create the certificate:

```bash
sudo openssl x509 -req -in local.minutestomidnight.co.uk.csr -CA m2mCA.pem -CAkey m2mCA.key
-CAcreateserial -out local.minutestomidnight.co.uk.crt -days 1825 -sha256 -extfile minutestomidnight.ext
```

You should be prompted for your CA private key passphrase. I now have three files:

1. local.minutestomidnight.co.uk.key (the private key)
2. local.minutestomidnight.co.uk.csr (the certificate signing request)
3. local.minutestomidnight.co.uk.crt (the signed certificate).

Copy those files to `/private/etc/apache2/`. I can now configure my web server with the private key and the certificate.

## **Configure the Web Server**

Edit `httpd.conf` by uncommenting these lines:

```bash
LoadModule socache_shmcb_module libexec/mod_socache_shmcb.so
LoadModule ssl_module libexec/mod_ssl.so
Include /usr/local/etc/apache2/2.4/extra/httpd-ssl.conf
```

Then open the vhosts file, and create a virtual host for the local SSL site:

```
<VirtualHost *:443>
 DocumentRoot "your__document__root"
ServerName local.minutestomidnight.co.uk.com
  ServerAlias local.minutestomidnight.co.uk.*.xip.io
 SSLEngine on
  SSLCertificateKeyFile /private/etc/apache2/local.minutestomidnight.co.uk.key
 </VirtualHost>
```

Edit `httpd-ssl.conf` and add the certificates to the local ssl site(s):

```
SSLCertificateFile "/private/etc/apache2/local.minutestomidnight.co.uk.crt"
SSLCertificateKeyFile "/private/etc/apache2/local.minutestomidnight.co.uk.key"
```

Test that everything in the configurations is okay with:

```bash
sudo apachectl configtest
```

It should return “Syntax OK”.

---

#macOS #Bash #CommandLine