---
title: Tell Us About Yourself
description:
date: 1970-01-01
tags:
  - jobs  
  - diary  
layout: layouts/post.njk
---

I have a blankout when a stranger asks me this, especially on a remote Zoom Call where I'm also being asked to whiteboard Fizz Buzz. A lot of stuff that happens, I forget it when asked about it later. I am jotting some *happenings* here therefore so in the future I may have fewer *wonderings*.

## Where are you at? What do you want?  What have you been learning?  
I want to be somewhere and be good at it.  This summer has been trying to find a parking spot. I thought my self learned LAMP stack was good but I lacked the kind of final year of college thing. I needed to go fuller in one direction. I had the curse of liking a lot of it.  Hence Drupal, Symfony hours of tutorials, full on data, all while job searching. All the while, I was misunderstanding Customer Service -- it's difficult and legit use of coding problem solving and it pays well.  

My identity goal might be: he's smart at something + at work, his phone never stops ringing. And provide for my family in a field with good pay that is not going away between now and 2040. And looking at narrow coding things that are over and done in 30 to 90 minutes.

Keep up my recreational 1 hour walk to coding -- that's my version of all that bike riding Dad always insisted on. Go poke around at code is my entertainment. That's my crossword puzzle. Unfortunately that will never build some big focused result.  That meshes really well with Customer Service in a role that touches something similar to a LAMP stack.  And probably not at someplace like a network troubleshooter: too far afield. Customer service at Cloudflare would be like starting all over again.  Same with 1010Data.  

## Story about a victory

Returning to Symfony, spinning up this http://clue.school project I made.  

### Story of proud coding: having a mental model of my remote server 

Starting in June, 2021 I'm super facile with __deploying__.  I impulsively bought three URLs, made an A record at the rackspace, made the DNS forwarding at the Domain Server, SSH'ing in and made a new server block in my Apache at the rack.  Did that all in less than an hour. Without looking ANYTHING up. Feels almost crazy that I could do that. End result: a URL that had never existed in the history of the world now exists and it says *hello*.


### Story 1 about hard work  
I have had a pretty constant coding habit.  The gaps in my repository commits came at three times this year when I was learning things that had little to do with commiting files:
1. Symfonycasts tutorials in May 2021  
2. Drupal tutorials in August 2021  
3.  Google Analytics, Tealium, and Matomo tag manager in October 2021  
{% image "github-heatmap-2021.png", "Heatmap of Evan Genest's activity at his GitHub repository" %}


### Story 2 about hard work  
I haven't conceptualized Working hard <----> Not working hard. I think ALL THE TIME about ticking off my to do list.  (Same as anyone in any job with any autonomy...)  My tools are different-time-of-day awareness: work great 6am to 10am and second burst from 3pm until 8pm.  And externalizing the task switcher: to a timer.  I recently stopped doing this with a spiral pad held down with a pomodoro paper weight. It's less organic/charming but Gnu Calendar is clean, great example of Gnu's design-sense and UI.  

Steven Covey's Seven Habits and Howard Gardener's lists (Getting Things Done) are ingrained in my strategies, for years now.

My lists and prioritizing system are iPhone lists and my bloggish things, incl Twitter and this blog here.  

Yes, focusing, not finishing the project, like https://clue.school...

After leaving my back end job in April 2021 I knew I needed a few weeks (months really but was impatient) of specific, added skills before I could apply succesfully for positions.  I circled my car around a parking lot: I did 3 week chunks of: __Symfony__ exercises/videos (shout-out to Ryan Weaver and Symfonycasts), __Drupal__ (many sources, shout out to some of the Template designers, to Evolving Web of Montreal, to OS Learning Drupal videos, to Web Wash), building out my sites at [Pikl](https://pikl.us/), [Drupal Farm](https://drupal.farm/), and [Clue School](https://www.clue.school/)

## Why did you leave your last job  
After a year and 3 months at OfficeSupply.com I got replaced by a developer with more experience: 5+ years versus my 0 years.  Things went well during my year there. I was proud when I began to get a signal for doing Code Reviews and making Pull Requests in their repo at Github:   

{% image "github-codereview-2020.png", "Pull Requests and Code Review by Evan Genest while a Back End Developer on the team at OfficeSupply.com in 2020" %}


### A tech problem I solved: good looking CSS   

A sign of my maturitty in web development: I switched from pridefully doing the CSS line by line to just grabbing resources.  
  
I was too prideful before to do this but also I didn't know resources. I went through a Bootstrap phase but am now down to things a fraction of that library in size: w3schools CSS and even smaller, the ______ (CSS library with South Asian name...).
  
[Clue School](https://www.clue.school/) came out looking good, for example.  For that I used a Template from W3Schools.

Started building Static Node.js web server: Eleventy too.  

## TELL ABOUT YOURSELF, Biz speak version: 
I was described by a recruiter as follows. It feels...strange. Helpful to know though the words for describing myself in biz-speak, knowing how the creatures of business speak to one another.  

*"Evan Genest has 3 years of experience in the industry. He is local to Madison, Wisconsin, and is very interested in hearing more about this opportunity with Foo Bar Baz."*

*"Evan is passionate about software support, in his role as a Customer Success Agent for Scooter Software, he was providing troubleshooting and support on their software, hardware, and infrastructure.  He conducted technical demos for clients, created technical documentation for power users, and has hands-on experience with database and server logs.  He's great with software, has a lot of experience working in SQL, performing manual testing, and ensuring customer satisfaction as often as he can."*

And then he skipped anything else, including my much harder job I went to after that. Keep it short, focused. Nobody wants to read more than five sentences. About anything.  

Not crazy about the word choice *passionate*, LOL. Ardent or conscientious maybe are okay, but I am not "passionate" about business correspondance. Intense and driven maybe, from the point of view of crossing tasks off of a todo list on my plate.  

Reading more Seth Godin books could cultivate an articulate version of the above, something more pleasant, less business drone.

### Errors and error messages

And just as good as those two things: little bugs in serving a first landing page from Twig are no big deal.  The error messages are not really enough to be docs.  You gotta already know the rough outline of which actors should be present.  All those months at DOI I would have to unspool the errors a line at a time with no knowledge of what was there.  YOu can't really backwards trace the breadcrumbs like that.  So...


I knew the db was missing, I knew how to pluck the right line from the SQLIte, MYSql, the defaulted PostGres, et al.  And then with no hints in that code, know enough to go put it in .env.local, not where it was uncommented from.  And know what to .gitignore and what not to.   

And the three branches to proceed down.  And how to know which methods are arriving in the IDE.   

The route worked in dev and then not in production.  https://clue.school/notes  I easily could picture the route serving of Symfony can't happen correctly with Apache heading things off at the pass.  Knew how to search site:symfony.com   And upon finding the stuff was not tempted to write it down "phonetically" as I even would have in May.  

