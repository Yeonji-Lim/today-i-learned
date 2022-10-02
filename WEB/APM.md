# APM
Apache, PHP, MySQL 이 세가지가 있으면 웹

Apache
web server

PHP -> Spring, node
was

MySQL 
DB

PM의 버전은 맞추어주어야 함 -> 연동이 되는게 있고 아닌게 있고 그럼
홈페이지에 어떤 DB와 잘 연동이 되는지 적혀있다.

소스 설치 -> 다운 압축풀고 환경변수 등록, config 수정 -> cli에 익숙해지게

## 구축

### Apache
```shell
brew install httpd
```
![[Pasted image 20220929224901.png]]
```shell
==> **Caveats**

DocumentRoot is /usr/local/var/www.

  

The default ports have been set in /usr/local/etc/httpd/httpd.conf to 8080 and in

/usr/local/etc/httpd/extra/httpd-ssl.conf to 8443 so that httpd can run without sudo.

  

To restart httpd after an upgrade:

  brew services restart httpd

Or, if you don't want/need a background service you can just run:

  /usr/local/opt/httpd/bin/httpd -D FOREGROUND

==> **Summary**

🍺  /usr/local/Cellar/httpd/2.4.54_1: 1,662 files, 31.7MB

==> **Running `brew cleanup httpd`...**

Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.

Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).
```

### PHP
```shell
brew install php@8.0
```

![[Pasted image 20220929224958.png]]
```shell
==> **php@8.0**

To enable PHP in Apache add the following to httpd.conf and restart Apache:

    LoadModule php_module /usr/local/opt/php@8.0/lib/httpd/modules/libphp.so

  

    <FilesMatch \.php$>

        SetHandler application/x-httpd-php

    </FilesMatch>

  

Finally, check DirectoryIndex includes index.php

    DirectoryIndex index.php index.html

  

The php.ini and php-fpm.ini file can be found in:

    /usr/local/etc/php/8.0/

  

php@8.0 is keg-only, which means it was not symlinked into /usr/local,

because this is an alternate version of another formula.

  

If you need to have php@8.0 first in your PATH, run:

  echo 'export PATH="/usr/local/opt/php@8.0/bin:$PATH"' >> ~/.zshrc

  echo 'export PATH="/usr/local/opt/php@8.0/sbin:$PATH"' >> ~/.zshrc

  

For compilers to find php@8.0 you may need to set:

  export LDFLAGS="-L/usr/local/opt/php@8.0/lib"

  export CPPFLAGS="-I/usr/local/opt/php@8.0/include"

  

  

To restart php@8.0 after an upgrade:

  brew services restart php@8.0

Or, if you don't want/need a background service you can just run:

  /usr/local/opt/php@8.0/sbin/php-fpm --nodaemonize
```

### Apache configuration

```shell
code /usr/local/etc/httpd/httpd.conf
```

