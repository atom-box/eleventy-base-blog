---
title: In Matomo How Do I Create a New Event and Goal
description:  Taking notes while listening to Ronan Chardoneau videos
date: 2022-11-12
tags:
  - web analytics
  - matomo

layout: layouts/post.njk
---

## Create a Goal
It is tempting to start here, but you may need to define the event for Matomo Analytics first.  

There are six default types of goals, found in the menu at Matomo >> Goals >> Add a new goal: 
* Visit a given URL
* Visit a given Page Title
* Send an event <======*this is the powerful part*
* Download a file
* Click on a Link to an external website
* Stay for a certain amount of time

## Create an Event
Why go through the effort to make Events? Why not just read the great default stats?  
  
Matomo says it well: 
```
100 people may visit your homepage for 20 minutes, but you won’t necessarily know what they were doing at that time. Did they simply walk away from the screen and grab a coffee? Or did they spend time watching a promotional video, which led to them starting to add their details to a newsletter subscription form which they couldn’t complete due to an error?
```


Examples of events: 
* leaving a comment
* scrolling 

Making an event requires some coding.  There are two options for this:  
* Add code to your actual HTML page or
* Add code in Tag Manager

The latter is the best!  



## Matomo documentation:  
https://matomo.org/web-analytics-training/  
https://matomo.org/faq/reports/create-a-goal-in-matomo/  
https://matomo.org/guide/reports/event-tracking/  

