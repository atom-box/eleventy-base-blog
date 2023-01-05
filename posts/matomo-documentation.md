---
title: Troubleshooting Tips for Matomo Web Page Analytics
description:
date: 2021-11-14
tags:
  - web analytics
  - matomo
layout: layouts/post.njk
---

## What this article is

I don't recommend reading this article, it is a personal souvineer so I can look back in the future and see where I have been, what I was learning month to month. Now I am learning the web analytics platform Matomo.  
  

## Best place to read about Matomo  
If *you* want to learn about Matomo, go to the official help site itself. Make this page your home page for explorations, it leads to all of the good stuff: https://matomo.org/help/    
  
The Help docs are readable, organized, clear.  And if you go down the many roads, the site is enormous, but upon first arriving, it doesn't feel enormous.  You only encounter the enormity once you go to your section of interest.  Once there, things can go deeper and deeper. But only if you keep digging.  The overall UX is excellent, in other words: the site opens up like a fractal in a video game where you walk closer and closer to a distant cliff in the video game and the landscape resolution keeps improving.   
  
What follows is a random fly by of Matomo's docs.  

## What to do when there is a data loss
[Nell Patel](https://neilpatel.com/blog/google-analytics-data-errors/)  
[Sarah Berry](https://www.webfx.com/blog/marketing/why-is-my-website-traffic-going-down/)  
[Taavi Kalvi](https://holini.com/website-traffic-drop/)  
  

## Glossary of Analytics Terms  
There is a helpful glossary with ~200 terms.  
https://glossary.matomo.org/  


## Ten common examples to *troubleshooting* actions
Find the pattern in where to look, what to check, what to ask. These solutions can be extended to other, seemingly novel problems:  

1. After updating, Matomo stopped working
- clear your cache (CTL-SHIFT-DEL)
- try a different browser
- in your Matomo installation delete files in `matomo/tmp/*`  
2. General strategy for Matomo errors: check PHP errors  
- find your php.ini file location and its error setting
```
$ php -r "phpinfo();" | grep php.ini
$ php -r "phpinfo();" | grep error
```
- turn error dispay on. Maybe send the errors to a log and then read that log.  
A nice guide to php error display is at https://www.freecodecamp.org/news/how-to-display-php-errors-and-enable-error-reporting/
- then check your server logs for server errors
3. You can always reinstall. Remove the Matomo directory and load the latest version  
4. The dashboard [looks weird](https://matomo.org/faq/troubleshooting/faq_135/) or is missing styling or portions
- check adblocker 
- some [libraries](https://matomo.org/faq/troubleshooting/faq_34/) may need to be installed  
5. Some pages are not being counted
- long URLs over 1024 are set to truncate. This setting can be changed.
6. IP address (and location, therefore?) is wrong. Like it's always the same IP.  
https://matomo.org/faq/troubleshooting/faq_17710/  
Proxy in front of your server may cause this. 
Using the API may cause this.  
See the docs for ways to overwrite this with the correct IP address.  
7. Geo-location not correct
- Is it turned on correctly in the settings?
- Look for Javascript errors in your console.  
- Set to track correct website?  
8. Referrer information is incorrect or missing  
- does your site have a redirect?
- do your visitors come from https and then pass first through an http at your site? This loses the referrer 
- did you put the tracking code (JS) into the right part of your page? It won't work inside an iFrame  
9. Matomo just gives a white-screen-of-death or a 500 error   
- first, enable auto [archiving](https://matomo.org/faq/troubleshooting/faq_19489/)
- if that doesn't help find your error in your server's error log. Use that to proceed in the Matomo FAQs, Forums, and Issues lists.  One bruteforce way to search multiple locations is to use SITE in a search engine. For example: `my error message site:matomo.org`  
10. You are getting more discrepency than expected between Matomo and another web analytic (i.e. Google Analytics)  
Causes of discrepent tracking:  
- 5% to 10% is normal. So don't even bother checking anything
- respecting (or not) the *Do not track* requests
- counting (or not) spiders and bots (Matomo doesn't count these)  
- is either service actually counting from a log (done to preserve privacy / avoid cookies)? Logs count things like file.css, file.js as *hits*, leading to inflated counting.
- one is a sample, other is a census  
- you set the IP exclusion listings differently or not at all
- are the JS scripts located in the same part of the page or possibly absent on some pages on one data analyzer?
- where on the page is the script? you have to locate it consistantly across the two analyzers  

# General places to go

## Issues at GitHub  

https://github.com/matomo-org/matomo/issues  


## Forum: Most-asked questions in the forum

It is awesome to see that the [forum](https://forum.matomo.org/) is sortable by most viewed, most replied, and date.

Most highly viewed in __General__ thread:  
Tag Manager questions, generally   
React app  
Tag manager blank screen  
Tracking Wordpress user ID with Tag Manager  
How to get data attribute in Custom JavaScript variable?  
Click trigger target data attribute  
https://forum.matomo.org/c/tag-manager/19?order=views  



## FAQs
There are 950 [Frequently Asked Questions](https://matomo.org/faq/).  
The categories of FAQs are  

    New to Matomo
    Installation
    Update
    How to
    Plugins and Themes
    Matomo on Windows
    Tag Manager
    General
    Troubleshooting
    Funnels
    Video & Audio Analytics
    Users Flow
    A/B Testing – Experiments
    Advertising Conversion Export
    Custom Reports
    Roll-Up Reporting
    Form Analytics
    Heatmap and Session Recording
    SEO Web Vitals
    Search Engine Keywords Performance
    Multi Channel Conversion Attribution
    SAML Login
    Log Analytics tool
    Mobile App
    Matomo for WordPress



## Tag Manager videos

These are in the [Help Centre](https://matomo.org/tag-manager-training/)  
Total running time (for 11 videos): 66 minutes  
https://matomo.org/tag-manager-training/  


Tag Manager videos table of contents:

    01. Introduction to Tag Manager systems
    02. Introduction to Matomo Tag Manager
    03. Deploying your first Container
    04. Tag Manager use case
    05. Tags
    06. Triggers
    07. Variables
    08. Versions
    09. Preview, Debug, Publish
    10. Data Layers
    11. Training conclusion


## Web Analytics videos

These are in the [Help Centre](https://matomo.org/web-analytics-training/).  
Total running time (for 19 videos): 118 minutes
Table of contents:  

Section one – understanding web analytics

    01. What is digital analytics?
    02. What is Matomo Analytics?

Section two – understanding Matomo features

    03. Making sense of the Matomo reports
    04. Tracking Goals
    05. Tracking Events
    06. Segments
    07. Funnels for Goals
    08. Users Flow
    09. Heatmaps & Session Recordings
    10. Media Analytics
    11. Form Analytics
    12. Search Engine Keywords Performance
    13. Custom Reports
    14. Roll-Up Reporting
    15. Multi Channel Conversion Attribution
    16. A/B Testing
    17. Activity Audit Log
    18. White Label
    19. Training conclusion

## Secret Videos
These are not secret, they are just one level deeper in the site navigation  

Videos in the [User Guides](https://matomo.org/docs/):

    Welcome to Matomo
    How to Install Matomo Analytics using Cloud-Hosted
    How to Install Matomo Analytics using Self-Hosted
    Matomo’s Visitors Feature
    Matomo’s Behaviour Feature
    Matomo’s Acquisitions Feature
    Matomo’s Ecommerce Feature
    Matomo’s Goals Feature
    Matomo’s Multi Attribution Feature
    Matomo’s Funnels Feature
    Matomo’s Media Analytics Feature
    Matomo’s A/B Testing Feature
    Matomo’s Form Analytics Feature
    Matomo’s Heatmaps Feature
    Matomo’s Session Recordings Feature
    Matomo’s Custom Reports Feature
    Matomo’s Tag Manager
    Matomo and the GDPR
    Importing Google Analytics data into Matomo
    Matomo Analytics for WordPress

# Random things I noted 

## Your db is not infinite! Periodically delete the older data

If you have properly setup the auto archiving script (see important note), you will still access all historical reports (even when RAW data is deleted). Delete the raw data in SQL, or the command line, or in the GUI dashboard.  
https://matomo.org/faq/troubleshooting/faq_42/  

## Random fact from the forums: CDN can affect analytics

In Matomo page views can become less than Visitors, due to the CDN
https://forum.matomo.org/t/more-visists-than-pageviews-how-is-this-possible/43717  


## Going 100% Cookieless

To avoid needing a banner on sites, users can go cookieless.  
    
Cookieless options in Matomo:

* If using the JavaScript tracker you simply disable cookies for all visitors. This comes at a cost to report accuracy.
* You can use Log Analytics to generate all reports from web server logs like Apache and Nginx without using any JavaScript tracker.
* Track your visitors with SDKs directly from within your application (for example PHP, C#, Java).

## Language of questions asked at the Matomo site
The site is mainly in English but the [user forum](https://forum.matomo.org/) posts for the last 30 days are also: 15 German, 4 French, 52 Spanish, 34 Italian
