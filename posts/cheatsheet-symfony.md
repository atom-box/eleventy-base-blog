---
title: Evan's Symfony cheatsheet
description:
date: 2021-02-05
tags:
  - symfony
  - drupal
  - cheatsheet
layout: layouts/post.njk
---

## Console Commands

```
php bin/console app:create-user

php bin/console cache:clear
```

## Twig

Basics
```

```

## Apache

Apache2 does not work out of the box with Symfony. How could it: both are trying to listen and respond to routes.

I had good success by just doing this:

1. Adding the symfony module for apache:
`composer require symfony/apache-pack`
2. In just the 443 (secure socket) Apache config I pasted, right after the DocumentRoot, this:
```
    <Directory /var/www/project/public>
        AllowOverride All
        Order Allow,Deny
        Allow from All
    </Directory>
```
## Unit testing

### Install PHPUnit

`wget https://phar.phpunit.de/phpunit.phar`

`chmod +x phpunit.phar`

`sudo mv phpunit.phar /usr/local/bin/phpunit`

`phpunit --version`

[https://www.startutorial.com/articles/view/phpunit-beginner-part-1-get-started](https://www.startutorial.com/articles/view/phpunit-beginner-part-1-get-started)

* Bug: the fake test example in the above link was written without a return type in the signature. Can fix the non runnable test by changing

`    protected function setUp()` signature  

to say `    protected function setUp(): void`

* Bug: arguments

```
$ php bin/console cache:clear

In DefinitionErrorExceptionPass.php line 54:
                                                                                            
  Cannot autowire service "App\Controller\CornellController": argument "$inputtedText" of   
  method "__construct()" is type-hinted "string", you should configure its value explicitl  
  y.                                                                                        
         
```
Solution: I put a `=` default value in the args

* Bug: Class not found  

Solution: Carefully check for agreement vis a vis the __USE__ and __NAMESPACE__statements for exact path agreement, like: /App/Controller   versus  just /Controller.   
Disagreement between __USE__ and __NAMESPACE__ burned up 90 minutes just now.  

* Wondering: setup and teardown seem a bit optional
PhpUnit works, even though I removed the following from the test  
```
    // protected function setUp(): void
    // {
    //     $speechScript = "Take me to the Limburger I saw so often in the past.";
    //     // $this->get('app.cornell');
    //     $cornellian = new CornellController($speechScript);
    // }
 
    // protected function tearDown(): void
    // {
    //     $this->cornellian = NULL;
    // }
```

## TDD

Writing the first few tests [like this](https://phpunit.de/getting-started/phpunit-9.html)     


## Service container and services.yaml

At the top of the block where you'll need the service, put a `$this->get(??)` where the arg tells us the name we used, back in `services/config.yaml`   
[Configuring Symfony](https://symfony.com/doc/current/configuration.html)
[44 minutes](https://www.youtube.com/watch?v=ucfgf9mkxfs) video from Peter Fisher  

## References

Best non Symfony is [ZetCode](https://zetcode.com/php/twig/)  by Jan Bodnar