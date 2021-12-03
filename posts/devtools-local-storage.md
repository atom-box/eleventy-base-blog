---
title: DevTools Local Storage
description:
date: 2021-12-03
tags:
  - javascript
  - web analytics
  - computer worksheet homework
  - AP Computer Science Principles
layout: layouts/post.njk
---

## Methods
* localStorage.getItem(key)
* localStorage.setItem(key, value)
* localStorage.removeItem(key)
* localStorage.clear()

## Browse the storage
Local storage is easy to browse in the devtools. In Firefox:  
`Devtools->Storage`  
Will reveal several types of stored things:  
* Cookies
* Cache
* Indexed DB
* Local storage
* Session storage

## Exercise to try
Here is some cookies based homework . 
1. Go to your browser's cookies list: `Settings->Privacy&Security->Cookies->ManageCookies` (in Firefox)
2. (optional) If you don't have many cookies, get some. Go to commercial sites: Amazon, OfficeSupply.com. Go to some high content story sites: vox.com, scoutingmagazine.org/ your local newspaper, yahoo.com. Do some browsing to accumulate some cookies 
3. Look at pairs of sites.  For their cookies, describe what is the same and what is different (do this in any way that makes sense for you, think of your audience, get your ideas across any way you prefer). Choose sites with 2 or more cookies.  
a. two sites that sell things  
b. a high traffic site and a less high traffic site  
c. two sites with URLs ending in .edu domain (If stumped you can find these by putting "site:.edu into Duck Duck Go or Google")  
d. two sites with a URL ending in the *.gov* domain  

## Another exercise to try
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
