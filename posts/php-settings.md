---
title: PHP Settings
description:
date: 2023-01-11
tags:
  - linux

layout: layouts/post.njk
---

## Updating my hosted server
sudo a2enmod proxy_fcgi setenvif  
sudo a2enconf php8.0-fpm  
sudo systemctl reload apache2  

See which versions of PHP are installed.  
$ ls /usr/bin/php*
  
```
$ sudo update-alternatives --set php /usr/bin/php8.1 
update-alternatives: using /usr/bin/php8.1 to provide /usr/bin/php (php) in manual mode
evan@nodejs-nyc:~$ php -v
PHP 8.1.14 (cli) (built: Jan  6 2023 15:22:36) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.14, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.14, Copyright (c), by Zend Technologies

```