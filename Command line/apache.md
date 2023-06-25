# Apache

## Process Name

```bash
httpd
```

## Start/Stop/Restart Apache

```bash
sudo apachectl start
sudo apachectl stop
sudo apachectl restart
```

## Find Apache Version

```bash
httpd -v
```

## Help

```bash
# Verify that an Apache process is listening on port 80
apachectl -h or: $ httpd -h
```

```bash
sudo lsof -iTCP:80 -sTCP:LISTEN
```

## Path to Apache

```bash
/etc/apache2/
```

## Path to Apache Configuration

```bash
/etc/apache2/httpd.conf
```

## Path to php.ini (php configuration)

```bash
/etc/php.ini
```

## Path to Apache Virtual Host Configuration

```bash
/etc/apache2/extra/httpd-vhosts.conf
```

## Path to Apache Logs

```bash
/etc/apache2/logs/
```

## Path to hosts file

```bash
# each virtual host MUST have a reference here, pointing to 127.0.0.1
/etc/hosts
```

## Tail errors in real time

```bash
cd /var/log/apache2
tail -f error_log
```

---

#Bash #CommandLine #Apache