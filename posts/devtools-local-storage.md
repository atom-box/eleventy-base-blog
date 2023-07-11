---
title: Introduction to Using DevTools to Investigate Browser Based Storage
description:
date: 2021-12-03
tags:
  - javascript
  - web analytics
layout: layouts/post.njk
---
## Use Devtools to see what the browser is storing
This is one of several articles for people wishing to try out different aspects of the devtools in Firefox.   

## Reading
When you use web pages and web applications what is stored in the Firefox or Chrome browser? Read some of the descriptions here:  
https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage  
https://www.w3schools.com/jsref/prop_win_localstorage.asp  
https://michellbrito.medium.com/localstorage-what-is-it-d589a0803de0  
https://blog.logrocket.com/localstorage-javascript-complete-guide/  



## Browse things stored in the client
Many objects (objects in a JS sense) are stored in the browser when you use a web page.  These are not hidden or mysterious. They are easy to browse in the devtools. In Firefox:  
`Devtools->Storage`  
Will reveal several types of stored things:  
* Cookies
* Cache
* Indexed DB
* Local storage
* Session storage

## Local Storage vs Cookies
https://en.wikipedia.org/wiki/Web_storage#Local_and_session_storage  
https://en.wikipedia.org/wiki/HTTP_cookie#Persistent_cookie    

## Local Storage Methods
* localStorage.getItem(key)
* localStorage.setItem(key, value)
* localStorage.removeItem(key)
* localStorage.clear()



## Cookie Exercise to try
Here is homework . 
1. Go to your browser's cookies list: `Settings->Privacy&Security->Cookies->ManageCookies` (in Firefox)
2. (optional) If you don't have many cookies, get some. Go to commercial sites: Amazon, OfficeSupply.com. Go to some high content story sites: vox.com, scoutingmagazine.org/ your local newspaper, yahoo.com. Do some browsing to accumulate some cookies 
3. Look at pairs of sites.  For their cookies, describe what is the same and what is different (do this in any way that makes sense for you, think of your audience, get your ideas across any way you prefer). Choose sites with 2 or more cookies.  
a. two sites that sell things  
b. a high traffic site and a less high traffic site  
c. two sites with URLs ending in .edu domain (If stumped you can find these by putting "site:.edu into Duck Duck Go or Google")  
d. two sites with a URL ending in the *.gov* domain  

## Local Storage exercise to try
4. Store a property. Get the browser console
```
 (Firefox: Ctl+Shift+I) -> Console  
```

Store your own silly property 
```
localStorage.setItem('froggy', 42);  
undefined  
```
Is the item still there? Check!
```
localStorage.getItem('froggy');
"false"  
```
Remove your made up proper property using any method listed above in the *Methods* section.  
Confirm it is gone, using something similar to `localStorage.getItem()` again.  

## Combined Exercise to try 
5. Use everything from above to look at some interesting large websites and see which properties that are typically stored in cookies versus which properties are typically stored in local storage.  This is open-ended; there is no *right* answer.