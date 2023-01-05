---
title: Using Google Ads and Matomo
description:  Taking notes 
date: 2022-12-09
tags:
  - web analytics
  - matomo

layout: layouts/post.njk
---

## Goal of tracking your ads
Reduce ad spend.  
Maximize the Return on Investment ratio.  

## The final URL of the Google Ad should get a suffix
The suffix brings over one or more JS variables.
* mtm_campaign  A string, the name of the campaign (required)
* mtm_kwd 
* mtm_source
* mtm_medium
* mtm_content
* mtm_cid "Click ID identifier", the only non-string JS property
  
Fun: your old versions of the above, written as UTM will work in Matomo. No rewriting needed.  
  
What if your existing tags have further parameters? You can customize Matomo to recognize those.  It takes a bit of setting up.  
    
A tool in Matomo: Acquisition >> "Campaign URL Builder"
  
Matomo can accept "whatever".  Add more variables here https://matomo.org/faq/how-to/faq_120/
  
## Example of a tag
### Before
https://your-website.com/

### After
https://your-website.com/?mtm_campaign=Name-Of-Your-Campaign&mtm_kwd=Your-Keyword&mtm_source=google&mtm_medium=cpc&mtm_content=My-Ad-Headline&mtm_cid=abc_1234567

## How to use Matomo to track Google Ads conversions without a Google tag
Tired: Sending a convert signal back to the Advertisement by putting Google's invasive tag (and 3rd party cookie) in your site         
Wired: Sending a convert signal back to the Advertisement by Google-Click-Identifier (GCLID).

How it works:  
1. A visitor arrives at your site, www.example.com, having clicked an ad.  They came from a link in a Google Ad similar to www.example.com/?gclid=123abc.
2. They travel around your site, eventually triggering your defined conversion  [Goals & Conversions](https://matomo.org/faq/reports/create-a-goal-in-matomo/)
3. Matomo will use the goals settings (you must set these up by hand) to send the following back to Google (with no need for an invasive Google 3rd Party cookie):
* that gclid 
* conversion time, 
* conversion value (if defined), 
* conversion currency and 
* conversion name
  
The following conversion export destinations are supported similarly:  
* [Google Ads ad conversion from Matomo](https://matomo.org/guide/manage-matomo/advertising-conversion-export/)  
* [Yandex ad conversion from Matomo](https://matomo.org/guide/manage-matomo/advertising-conversion-export/)  
* [Microsoft ad conversion from Matomo](https://matomo.org/guide/manage-matomo/advertising-conversion-export/)   
* [Facebook ad conversion from Matomo](https://matomo.org/guide/manage-matomo/advertising-conversion-export/) 

In your Google Ads interface, additional data will be visible:  
* the landing page that resulted in the conversion  
* the keyword that was used  

The normal pipeline to Google, from Matomo, is to tell Google Ads your API URL in Matomo, for a Scheduled import via HTTPS.

The main point of all this bears repeating:  
When you have this feature, then you get back the insights of which online ads are successful without needing to embed anything from a third party network.