---
title:  Matomo specs and dependencies
description: Beginners Guide How to Install Matomo analytics
date: 2021-11-12
tags:
  - web analytics
  - matomo
layout: layouts/post.njk
---

## Some ideas about Matomo Installation 
Q: Why is 50,000 views a month the upper limit of recommended installs on [the WP module](https://matomo.org/download/)?  
A: Server might not be able to store that much data.   

## Size of the Matomo download __on the server__

79460kB (79MB)  

## Size of what is loaded to browser  
The client in each case gets ever smaller downloads:  
- Google Analytics 40kB
- Matomo Analytics 20 kB
- Plausible Analytics 1 kB  
(source: Plausible team talking on the Changelog podcast)  
Caveat: I don't know if Mobile download is different.  


## Node modules and sizes in Matomo

28      matomo/node_modules/jquery-mousewheel
36      matomo/node_modules/qrcodejs2
68      matomo/node_modules/ng-dialog/js
224     matomo/node_modules/ng-dialog
24      matomo/node_modules/angular-sanitize
48      matomo/node_modules/chroma-js
340     matomo/node_modules/jquery-ui-dist
196     matomo/node_modules/angular
32      matomo/node_modules/mousetrap
44      matomo/node_modules/angular-animate
36      matomo/node_modules/jquery.scrollto
160     matomo/node_modules/angular-mocks
28      matomo/node_modules/visibilityjs/lib
36      matomo/node_modules/visibilityjs
24      matomo/node_modules/jquery/external/sizzle/dist
32      matomo/node_modules/jquery/external/sizzle
36      matomo/node_modules/jquery/external
88      matomo/node_modules/jquery/dist
148     matomo/node_modules/jquery
12      matomo/node_modules/sprintf-js/dist
28      matomo/node_modules/sprintf-js
8       matomo/node_modules/jquery.browser/dist
28      matomo/node_modules/jquery.browser
12      matomo/node_modules/jquery.dotdotdot/src
12      matomo/node_modules/jquery.dotdotdot/dist
44      matomo/node_modules/jquery.dotdotdot
20      matomo/node_modules/angular-cookies
40      matomo/node_modules/iframe-resizer/js
104     matomo/node_modules/iframe-resizer
184     matomo/node_modules/materialize-css/dist/js
144     matomo/node_modules/materialize-css/dist/css
332     matomo/node_modules/materialize-css/dist
364     matomo/node_modules/materialize-css

## Symfony modules and sizes in Matomo

28      matomo/vendor/symfony/polyfill-ctype
4       matomo/vendor/symfony/console/Symfony/Component/Console/Resources
56      matomo/vendor/symfony/console/Symfony/Component/Console/Descriptor
8       matomo/vendor/symfony/console/Symfony/Component/Console/Logger
12      matomo/vendor/symfony/console/Symfony/Component/Console/Tester
36      matomo/vendor/symfony/console/Symfony/Component/Console/Output
32      matomo/vendor/symfony/console/Symfony/Component/Console/Command
32      matomo/vendor/symfony/console/Symfony/Component/Console/Formatter
144     matomo/vendor/symfony/console/Symfony/Component/Console/Helper
72      matomo/vendor/symfony/console/Symfony/Component/Console/Input
20      matomo/vendor/symfony/console/Symfony/Component/Console/Question
20      matomo/vendor/symfony/console/Symfony/Component/Console/Event
504     matomo/vendor/symfony/console/Symfony/Component/Console
508     matomo/vendor/symfony/console/Symfony/Component
512     matomo/vendor/symfony/console/Symfony
516     matomo/vendor/symfony/console
12      matomo/vendor/symfony/event-dispatcher/Symfony/Component/EventDispatcher/DependencyInjection
24      matomo/vendor/symfony/event-dispatcher/Symfony/Component/EventDispatcher/Debug
88      matomo/vendor/symfony/event-dispatcher/Symfony/Component/EventDispatcher
92      matomo/vendor/symfony/event-dispatcher/Symfony/Component
96      matomo/vendor/symfony/event-dispatcher/Symfony
100     matomo/vendor/symfony/event-dispatcher
64      matomo/vendor/symfony/polyfill-mbstring/Resources/unidata
68      matomo/vendor/symfony/polyfill-mbstring/Resources
132     matomo/vendor/symfony/polyfill-mbstring
8       matomo/vendor/symfony/monolog-bridge/Symfony/Bridge/Monolog/Handler/FingersCrossed
36      matomo/vendor/symfony/monolog-bridge/Symfony/Bridge/Monolog/Handler
8       matomo/vendor/symfony/monolog-bridge/Symfony/Bridge/Monolog/Formatter
8       matomo/vendor/symfony/monolog-bridge/Symfony/Bridge/Monolog/Processor
72      matomo/vendor/symfony/monolog-bridge/Symfony/Bridge/Monolog
76      matomo/vendor/symfony/monolog-bridge/Symfony/Bridge
80      matomo/vendor/symfony/monolog-bridge/Symfony
84      matomo/vendor/symfony/monolog-bridge
1520    matomo/vendor/symfony/polyfill-iconv/Resources/charset
1524    matomo/vendor/symfony/polyfill-iconv/Resources
1572    matomo/vendor/symfony/polyfill-iconv
2436    matomo/vendor/symfony






