---
title: Quick survey of the Javascript loaded by the Tealium demo page
description:
date: 2021-11-04
tags:
  - web analytics
layout: layouts/post.njk
---

## Analyzing the Tealium eCommerce Demo Page

### Visit the page  
Tealium has a fake page for playing with tag placement: [https://ecommerce.tealiumdemo.com/](https://ecommerce.tealiumdemo.com/)  
I'm just interested in which JS is running gthe Tealium web analytics.

### List *all* of the scripts that get loaded

```html
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/js/prototype/prototype.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/js/lib/jquery/jquery-1.12.1.min.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/js/lib/jquery/noconflict.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/js/lib/ccard.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/js/prototype/validation.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/js/scriptaculous/builder.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/js/scriptaculous/effects.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/js/scriptaculous/dragdrop.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/js/scriptaculous/controls.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/js/scriptaculous/slider.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/js/varien/js.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/js/varien/form.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/js/mage/translate.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/js/mage/cookies.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/skin/frontend/rwd/default/js/lib/modernizr.custom.min.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/skin/frontend/rwd/default/js/lib/selectivizr.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/skin/frontend/rwd/default/js/lib/matchMedia.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/skin/frontend/rwd/default/js/lib/matchMedia.addListener.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/skin/frontend/rwd/default/js/lib/enquire.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/skin/frontend/rwd/default/js/app.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/skin/frontend/rwd/default/js/lib/jquery.cycle2.min.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/skin/frontend/rwd/default/js/lib/jquery.cycle2.swipe.min.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/skin/frontend/rwd/default/js/slideshow.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/skin/frontend/rwd/default/js/lib/imagesloaded.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/skin/frontend/rwd/default/js/minicart.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/skin/frontend/base/default/js/msrp.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/skin/frontend/rwd/default/js/msrp_rwd.js"></script>
  var _syncstr = "https://tags.tiqcdn.com/utag/" + o.account + "/" + o.profile + "/" + o.env +"/utag.sync.js";
```

I am only interested in what talks to Tealium.  

Most of that Javascript is just libraries for making the page work:  
**MSRP** is for sockets and streams (Message Session Relay Protocol).  
**Scriptaculous** is a JQuery type thing, kind of from the same era.  
**JQuery** is JQuery.  
**RWD** is a library for Responsive Web Design.  
**Mage** may be connected to the Node.js game framework? Maybe?  
**Varien** is a library that's been around, especially used for ecommerce, like form validation, I think.  

That leaves  
```html
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/js/prototype/prototype.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/js/lib/ccard.js"></script>
<script type="text/javascript" src="https://ecommerce.tealiumdemo.com/js/prototype/validation.js"></script>
  var _syncstr = "https://tags.tiqcdn.com/utag/" + o.account + "/" + o.profile + "/" + o.env +"/utag.sync.js";
```
  
That last line seems to be the money shot for our purposes: 

For a 404 error (`https://tags.tiqcdn.com/utag/foooo/barrrrr/bazzzzz/utag.sync.js`) the server returns zero characters, other than the commented header:
```json
//tealium universal tag - utag.sync ut4.0.202110291804, Copyright 2021 Tealium.com Inc. All Rights Reserved.
```

However if the o object is intialized with:  
{
    "account": "tealiumlabs",
    "profile": "commerce",
    "env": "prod"
}

the Tealium server returns:
```js
//tealium universal tag - utag.sync ut4.0.202109220846, Copyright 2021 Tealium.com Inc. All Rights Reserved.
try {
    try {
        window.optimizely = window.optimizely || [];
        var __tealium_va = JSON.parse(localStorage.getItem('tealium_va'));
        if (__tealium_va && __tealium_va.badges) {
            if (__tealium_va.badges['5142']) {
                window.optimizely.push(['addToAudience', 8008019481]);
            };
            if (__tealium_va.badges['5127']) {
                window.optimizely.push(['addToAudience', 3245770086]);
            };
        }
        document.write('<scr' + 'ipt type="text/javascript" src="//cdn.optimizely.com/js/7777000011.js"></scr' + 'ipt>');

    } catch (e) { console.log(e) }
} catch (e) {
    console.log(e);
}
```
Minor: those lines seem to redundantly wrap *try-catch* (2x) -- maybe as a weird bug fix for something?  
Minor: those lines check which badges are present (5142 present? 5127 present?), and if they are, loads 'addToAudience' for each onto the *__tealium_va* object.  

Major: the whole point here is to load the main Tealium client-side product, 12000 lines of Javascript, from https://cdn.optimizely.com/js/7777000011.js.  
View a prettified version of this at  
https://github.com/atom-box/7777000011 
