---
title: Tell me an example where you...
description:
date: 1970-01-01
tags:
  - jobs
layout: layouts/post.njk
---

A lot of stuff that happens, I forget it when asked about it later. I am jotting some *happenings* here therefore so in the future I may have fewer *wonderings*.

## Tell us about a victory

Date: 10-03-2021  

Returning to Symfony, spinning up this http://clue.school project I made.  

### Live all the parts making a URL

I'm super facile with __deploying__.  I impulsively bought three URLs, made an A record at the rackspace, made the DNS forwarding at the Domain Server, SSH'ing in and made a new server block in my Apache at the rack.  Did that all in less than an hour. Without looking ANYTHING up. Feels almost crazy that I could do that. End result: a URL that had never existed in the history of the world now exists and it says *hello*.

### Looks great, quickly

Throwing together a whole clean __style__ I shopped around for "lightweight css template".  Got a whole framework and a great template.  Had the whole thing live and serving in production, including writing a bunch of content and figuring out that the icons were from 2017, v4 of fontawesome.  Did all that in 2 hours.  I used to take like a week to write the divs, the classes, get Gulpfile working.  Don't!  You're not applying for a CSS job!  Feels great!!

### Errors and error messages

And just as good as those two things: little bugs in serving a first landing page from Twig are no big deal.  The error messages are not really enough to be docs.  You gotta already know the rough outline of which actors should be present.  All those months at DOI I would have to unspool the errors a line at a time with no knowledge of what was there.  YOu can't really backwards trace the breadcrumbs like that.  So...


I knew the db was missing, I knew how to pluck the right line from the SQLIte, MYSql, the defaulted PostGres, et al.  And then with no hints in that code, know enough to go put it in .env.local, not where it was uncommented from.  And know what to .gitignore and what not to.   

And the three branches to proceed down.  And how to know which methods are arriving in the IDE.   

The route worked in dev and then not in production.  https://clue.school/notes  I easily could picture the route serving of Symfony can't happen correctly with Apache heading things off at the pass.  Knew how to search site:symfony.com   And upon finding the stuff was not tempted to write it down "phonetically" as I even would have in May.  

