---
title: De-Google With the Creators of Plausible
description: Notes condensed from listening to changelog podcast
date: 2021-11-12
tags:
  - web analytics  
layout: layouts/post.njk
---

These are notes summarizing [Episode 396](https://changelog.com/podcast/396) of the Changelog podcast: __De-Google-ing your website analytics__  with Marko Saric & Uku Täht.

How lightweight are Analytics? A comparison of the script loaded by each:  
Google analytics JS file: 47kB  
Matomo analytics JS file: 20 kB  
Plausible analytics JS file: 1kB  

GDPR compliance: of the above, only Plausible is cookie-free.  BUT this means it cannot do the real UX analysis tasks: heat maps, session recording.  Plausible also anonymizes more things: visitor ID and IP address are both anonymized.  

*(Plausible is too stripped down...seems like a good use case for lots of things that are developed by teams of one or two people. Any larger team would benefit from site insights from Matomo.)*  

## Alternatives to Google products  
### reCAPTCHA  
VisualCaptcha  
Honeypot  
hCaptcha  
Akismet Wordpress plugin  

### Google Analytics 
Matomo  
Plausible    
  
### Google fonts  
Download and self host from Google  
Use web safe fonts  
  
### Youtube  
Vimeo  
PeerTube  
  
### Google Maps  
OpenStreetMap  
Leaflet  
Mapbox  
  
### Anonymize IP addresses  
[use this code](https://support.google.com/  analytics/answer/2763052?hl=en)
  









