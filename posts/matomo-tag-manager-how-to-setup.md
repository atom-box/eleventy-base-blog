---
title:  Matomo Tag Manager How to set up
description: Foo bar baz.
date: 2023-01-13
tags:
  - web analytics
  - matomo
layout: layouts/post.njk
---

## Q: Which do I put in, the Matomo Tag, the MTM tag, both?  
 
## A: Here are examples of these two tags:    
### Here is the normal Matomo tag 
```
<!-- Matomo Tag Manager -->
   <script>
    var _mtm = window._mtm = window._mtm || [];
    _mtm.push({'mtm.startTime': (new Date().getTime()), 'event': 'mtm.Start'});
    var d=document, g=d.createElement('script'), s=d.getElementsByTagName('script')[0];
    g.async=true; g.src='https://littlefurnace.com/matomo/js/container_4hym701r.js'; s.parentNode.insertBefore(g,s);
   </script>
<!-- End Matomo Tag Manager -->
```
  
### Here is the tag manager tag
```
<!-- Matomo -->
  <script>
    var _paq = window._paq = window._paq || [];
    /* tracker methods like "setCustomDimension" should be called before "trackPageView" */
    _paq.push(['trackPageView']);
    _paq.push(['enableLinkTracking']);
    (function() {
      var u="//littlefurnace.com/matomo/";
      _paq.push(['setTrackerUrl', u+'matomo.php']);
      _paq.push(['setSiteId', '1']);
      var d=document, g=d.createElement('script'), s=d.getElementsByTagName('script')[0];
      g.async=true; g.src=u+'matomo.js'; s.parentNode.insertBefore(g,s);
    })();
  </script>
<!-- End Matomo Code -->  
```

  
 
YOU DON'T NEED BOTH.   
   
  
## Q: But when I took away the normal Matomo tag, I stopped getting data  
## A: You need to enable Matomo tracking *inside* of the Matomo Tag Manager.  

If you want to use the premium features tracking code they just need to tick the box to bundle matomo.js with their Tag Manager container. It doesn't need to be setup manually for the premium features using the API  In Tag Manager: create a container       Variables > Create New Variable > Matomo Configuration:          checkbox Bundle Tracker          checkbox Register as Default Tracker      Triggers > Create New Trigger > Pageview       Tags > Create New Tag > Pageview    If you skip 3, 4 you end up with no data layers on the pages and you'll have a bunch of zeroes in your dashboard.    If you do the above, you can remove from your pages the regular Matomo tag  
  
In general it is recommended to just have a single tracking script inserted into your website. When you insert multiple different tracking scripts it can start to cause some unexpected issues. A single tracking script (Either the tag manager or the standard javascript code) should be sufficient to track any data to your Matomo instance.  
  
If you want to use both the Matomo Tag Manager and the standard JavaScript tracker together on the same website, then this can easily be done.  All you need to do is ensure that the Matomo Tag Manager is not bundling the matomo.js file and that it is not registered as the default tracker, eg in the Matomo Variable make sure the following is not selected: 1) Bundle Tracker 2) Register as Default Tracker  


  



