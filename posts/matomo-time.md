---
title: Time Related Issues in Matomo
description:
date: 2023-05-15
tags:
  - matomo
layout: layouts/post.njk
---

## Why Are Visitors Staying on my Page for 0 Seconds 

Matomo puts a UTC time stamp when your visitor arrives on each page. It reports "time on page" by simply subtracting each arrival time.  "0 Seconds" will be the reported time for a page if it is either the ONLY page or the FINAL page.  
  
Fix this and make it accurate by adding a stopwatch: the javascript heartbeat: 
https://matomo.org/faq/how-to/faq_21824/
https://matomo.org/faq/how-to/faq_21158/   
https://forum.matomo.org/t/visit-duration-optimal-settings/47548 
  
A multi-tab example:   
Lets say I land on page A, and open page B,C,D in multiple tabs in quick succession from page A. Will the time spent on page B be calculated as the few seconds it took to open page C from page A? Or will it be NULL if B is the last page, and calculated compared to the next tab/page I open from page B?   
Matomo will calculate the time between "Pageviews" for subsequent pageview tracking requests. Using this example, if I enter through Page A and open pages B,C & D in order after each other in quick succession then the time on page will be calculated as the time between the Pageview tracking requests which would be a few seconds or less in this example.  
  
  
## Average Time on Page 
Average time on page in Matomo is currently not available in custom reports. The average time on page is in the back log for development. BUT in general it is already there at average per page is under behaviour >> pages.  

The Matomo bug fix, issue,s and feature requests for core (non-paid) features is here: 
https://github.com/matomo-org/matomo/issues
  

## Some time data to try

### Session time
visitors > visits log shows total time of a visit, but not per page time.   

### Segments can check time  
In top tab (segments) easy to make a condition VISITDURATION greaterThan 300 seconds. 

## What is the Time Delay of new stats

How often are reports generated refreshed?  For example, to see "live" tracking data of your website in the Matomo UI, you can use either the Visits Log, Real Time or Real Time Map reports. See this FAQ for more info: https://matomo.org/faq/general/faq_41/    The other reports such as the Pages, Page Titles, Events, etc. are what we call "Archived" or "Aggregated" reports. These reports in Matomo are not processed in real time and are processed using a scheduled task configured on the server. In an On-Premise setup, you can configure how often the reports are updated. With Matomo Cloud the reports for the "today" period are processed roughly once every 6 hours. Other periods are processed at different intervals. For these reports you can check how recently they were processed by clicking on the "i" icon: (blue circle glyph).
  

## In the SQL Table, Which Time Zone is used?
UTC is what Matomo stores as. All of the data in the Matomo database and data processed by the archiver is stored and processed in UTC. For the archiver logs this is important because certain tasks or actions are only completed once a day (Eg. the first time the task completes for that day). If the archiver logs were stored in the servers time zone then this would make it very challenging to troubleshoot certain things.  It's also important to understand that this is done because a single Matomo server can have many websites with various different time zones.

