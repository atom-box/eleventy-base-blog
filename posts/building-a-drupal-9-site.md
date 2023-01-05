---
title: Building a Drupal Site
description:
date: 2021-05-21
tags:
  - drupal
layout: layouts/post.njk
---


# Personal notes

These are mostly for me, maybe not readable by anyone else.

## How to make a thing that has many sibling things

1. Create content will have two options.  
2. Of these two options,  
    *create basic article* has options like tags and images built in,   
    *create basic page* has no images, no tags.  

Uploaded files and images can be browsed from Admin->Content->Files tab. They end up there automatically without you putting them there.

## How to make something that is one of a kind, siblingless

1.Make a custom block Structure->blocks->custom block
2.Place it            Structure->blocks->block layout

Don't think of blocks as content. They are more like a footer or sidebar or modal.

## An overview of how the UX planning goes when planning a site

I learned all this at a well-worth-it one week course from Evolving Web.  

Before starting to code, the site needs to be planned. Both a redesign or green field development can follow the steps below.  Notice that the actual coding comes pretty late in the sequence:

1. Questionaires.  Get out of your own head. The closer you get to what your real users are like the more they will enjoy what you build.
2. Develop fictional personas.
    - a random person who arrived by organic search
    - a current employee
    - a volunteer to your org
    - a job seeker
    - a potential customer
3. Map ideal journeys those personas would take on your site. What you're paid to do is align what the user feels is a happy experience and what your organization considers a happy experience. Notice we have not written any code yet.
4. Inventory the existing and potential content.
    - if a competitor site or your org's existing site are relevant you can inventory those. An automatic free tool for building a data tree of site content is at [Screaming Frog](https://www.screamingfrog.co.uk/seo-spider/#spider-features)
5. Architect your site. Design the relational database. Make wireframes.
6. Concept! Let the designers mock up some pages.
7. Develop. Realize the site in code.
8. Continuous Improvement.

## Here are the kinds of brainstorms that UX folks do

### Result of a team brainstorming session about user journeys
{% image "journeys-whiteboard-at-Miro.png", "A whiteboard with many completed post it notes and scribblings on it" %}

### Result of a team brainstorming session about user personas
{% image "personas-whiteboard-at-Miro.png", "A whiteboard with many completed post it notes and scribblings on it" %}

(Todo: activate [captions module](https://www.alpower.com/tutorials/adding-figures-with-captions-to-images-in-markdown-with-eleventy/) in Eleventy)

## Sources for these notes

Several dozen well organized videos are at https://www.youtube.com/watch?v=MXM3Ql1CqDg. They were made in 2016 by Acquia and OS Training.  They are similar (or maybe identical?) to the ones that exist behind the paywall at LinkedIn Learning.

The courses at [Evolving Web](https://evolvingweb.ca/training) are worth the money. Their courses are ~$400 for each one week course and they are live, so check the schedule.

