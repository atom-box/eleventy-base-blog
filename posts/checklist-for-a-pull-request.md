---
title: Pull requests checklist!
description: This is a post on My Blog about win-win survival strategies.
date: 2021-03-20
tags:
  - linux
  - hacktoberfest
layout: layouts/post.njk
---

When you submit a pull request, take time to make it look nice. Logic aside, there are some general things to do in any language before you ask someone else to do a code review of your work. These are things that I forget to do when I am in a hurry to have someone look at my code.

## Most Important

Even if you are sick of your code and if you are under deadline pressure, remember to do these things:

* Go read the original story. Did you answer the problem succinctly? In all the frenzy of your hacking, did the code creep beyond what the story asked for?
* Search your code for the word *todo*. Search for comments. It's embarrassing to leave in a note you wrote to yourself. You're also looking for things you turned off in the code; it's time to turn those back on.
* IMPORTANT Run the diff to highlight everything you changed. `git log master..develop` where *master* and *develop* are the names of your branches. This sounds like common sense but it can track down strange and subtle things you did that are hard to find otherwise. Did the cat run across the keyboard? Did you drag (or even delete) an entire line from nearby code?

## Less Important

These are still important but I think half of all programmers would not forget to do these things. For me, I need a list:

* Run the automated style checker for your local language and style. For CSS, PHP, and JS try [CodeSniffer](https://pear.php.net/package/PHP_CodeSniffer/). For HTML Squizlabs makes an [HTML_Sniffer](https://squizlabs.github.io/HTML_CodeSniffer/)
* Did you write enough unit tests?
* Run the existing unit tests in your automated test suite.
* Are there too many commits? Are all of the commits working code? Rollbacks to non-working commits aren't helpful during debugging. Consider using [squash](https://gitbetter.substack.com/p/how-to-squash-git-commits) -- it's not that hard.
* Lists of Imported files should be alphabetized. Watch out for whether your automated tools are alphabetizing by capital letters or not. Out of the box, VSCode does not comply with my team's style on this.
* Double check your whitespace. Is trailing space on the line end bad in your team? Is a concluding blank line as last line of code good? Are you consistantly using the semi-colon in JS? Most IDE's have a setting for fixing this during saving. In VSCode search for *whitespace* in the plugins.
* Variable naming is consistant with camelCase, snake_case, or kabab-case for this part of the code in your organization?

## Open Source Pull Requests

All of these things apply doubly to code that is being reviewed for an open source project like [Hacktoberfest](https://hacktoberfest.digitalocean.com/?ref=hackernoon.com). A stranger who is volunteering their time is unlikely to appreciate sloppiness in the code.
