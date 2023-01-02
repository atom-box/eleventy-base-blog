---
title: Notes on using Eleventy
description: Notes condensed from listening to changelog podcast
date: 2022-12-28
tags:
  - troubleshooting  
layout: layouts/post.njk
---

## Error: "TemplateLayoutPathResolver directory does not exist"
This went away when I moved my working directory one level higher; a bit embarrassed. 
  
In the future, might consider these also:
* Read the comment in the Eleventy issues: https://github.com/11ty/eleventy/issues/1642 
* DEBUG=Eleventy* npx @11ty/eleventy at the command line was interesting, though not useful 
* there are other compile commands, similar to 'npm dev' I think  

## Git commands that were useful during blog editing


* git reset is specifically about updating the index, moving the HEAD.
* git checkout is about updating the working tree (to the index or the specified tree). It will update the HEAD only if you checkout a branch (if not, you end up with a detached HEAD) -- (actually, with Git 2.23 Q3 2019, this will be git restore, not necessarily git checkout)
* By comparison, since svn has no index, only a working tree, svn checkout will copy a given revision on a separate directory.