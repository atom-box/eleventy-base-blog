---
title: Website of Representative Slotkin
description:
date: 2021-12-09
tags:
  - web analytics
  - drupal
layout: layouts/post.njk
---

The website for Congresswoman Elissa Slotkin is at https://slotkin.house.gov.  The following is what I learned by looking at its web design.

## UX 

The Elissa Slotkin site has a clean design. It seems aware that a third of its users are older folks.  

I have an octagenarian friend, so I will investigate the site's senior-friendliness by watching her navigate it this week when she tunes in to the upcoming livestream at http://slotkin.house.gov/live  

## Design and CSS
The use of Red and Blue are very balanced. This is not an blue heavy Squad or E Warren site: keeping the door open to Red and Blue folks.  

## Data Odometer Spinner
I don't know what this element is properly termed. It's a banner 2/3 of the way down many popular pages that shows animated loading numbers for how succesful the business is.  For this page, it animates three numbers:

    136,000
    Responses to Emails, Letters and Calls
    2,593
    Constituent Cases Closed
    $1,637,000
    Dollars Returned to Constituents


## Technology used by the site

According to [Built With](https://builtwith.com/slotkin.house.gov), the following things are in the stack of the Slotkin site.

### Varnish  
Varnish is a server, specialized in caching, maybe for video streaming especially? 

2000 of the top 10000 sites use a Varnish server (says Built With). 

*The name Varnish comes from when the instigator of Varnish spent a long time staring at an art-poster with the word "Vernissage" and ended up checking it in a dictionary, which gives the following three meanings of the word...* (https://varnish-cache.org/intro/) 

### Drupal

This continues my observation that there is always a job for you in government web development if you keep up with Drupal.  

The site is on an up to date Drupal 9 (yay!).

In theming I see there is a WooTheme style on the FlexSlider.  

### Javascript

* FlexSlider (jQuery slider)
* SuperFish (jQuery menu)
* Hover (*hoverIntent is a plug-in that attempts to determine the user's intent by monitoring onMouseOver.*)
* html5shivhtml5shiv (For Internet Explorer)
* Twitter PlatformTwitter (adds a stream of recent tweets) 
* Facebook for Websites (adds a stream of recent postings)
* Facebook SDK (*for authentication and sharing via the FB API*)
* JavaScript SDK enables you to access all of the features of the Graph API via JavaScript, and it provides a rich set of client-side functionality for authentication and sharing. It differs from Facebook Connect.

### Advertising
Federated Learning of Cohorts (FLoC) (*a privacy-preserving mechanism for interest-based ad selection*).  

It is an ethical advertising project, maybe like DuckDuckGo?  The [Readme at Github](https://github.com/WICG/floc) is helpful.

The total number of users of FLoC plummeted from 50,000 to 20,000 in August, according to the graph at BuiltWith. 

### Hosting
Nexcess  
And DNS from Azure maybe  

### Mapping by ArcGIS
This seems like a boss-move.  De-google your web pages everybody!

### Web Analytics
Oh. The Web Analytics is Google Tag Manager. 

