# Content and server for my blog

## This Blog

Tattl.me is my very modest blogging effort. It contains a few notes about web development. This blog is at [https://tatll.me](https://tatll.me)

## Contact me

I am at [Little Furnace](http://littlefurnace.com) 

## Generated with Eleventy

The blog pages are written in markdown and then generated with 11ty.    
   
Eleventy is a node.js server. To install it, go to a server location you own and in /var/www/blog (or similar) clone the official repository from the Eleventy [github repo](https://github.com/11ty/eleventy-base-blog)

## How to add content
Just copy any markdown file from `/posts` and then re-build the site by typing `npx eleventy`  

## How to view locally
During editing you can see the current built version of your site locally by just opening `/_site/index.html` in a browser. You don't need to point Apache at it or start a Node anything. It's a static site, just a bunch of linked files: there's no reason to have a server running.