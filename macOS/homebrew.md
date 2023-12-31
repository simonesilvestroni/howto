# Homebrew

- [Install homebrew from here](https://docs.brew.sh/Installation).
- Update: `brew update`.
- Upgrade formulas: `brew upgrade`.
- Check homebrew: `brew doctor`.

# Remove homebrew orphan dependencies

```
brew autoremove
```

# PHP in Homebrew

To enable PHP in Apache add the following to `httpd.conf` and restart Apache:
    
```
LoadModule php_module /usr/local/opt/php/lib/httpd/modules/libphp.so

<FilesMatch \.php$>
  SetHandler application/x-httpd-php
</FilesMatch>
```

Finally, check:

```
DirectoryIndex includes index.php
DirectoryIndex index.php index.html
```

The `php.ini` and `php-fpm.ini` files can be found under:

`/usr/local/etc/php/<PHPversion>/`

To start php now and restart at login:

```
brew services start php
```

---

#macOS #Bash #CommandLine