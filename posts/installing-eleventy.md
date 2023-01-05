---
title: Installing Eleventy
description:
date: 2021-09-17
tags:
  - linux
layout: layouts/post.njk
---

I followed the instructions in the [11ty Github repo](https://github.com/atom-box/eleventy-base-blog/blob/master/install.md).

## One bug

I set Apache wrong.  I fixed this by making the server point to the `_site` directory in the project, not to the top level of my project.

## How to configure input and output

Eleventy can consume and build to wherever you like. To do this, the root directory should have a file called `.eleventy.js`. In the example below we set the *input* and *output* directories to be `src` and `build`:

```js
// eleventy.js
module.exports = config => {

  // 11ty defaults
  return {

    dir: {
      input: 'src',
      output: 'build'
    }

  };
};

```

## Normal useage

1. A single blog post is written as its own markdown file. Save it in the directory `posts`
2. After saving it, rebuild the static site: `npx eleventy`

## Using an image

Bryce Wray described how to add the Eleventy module for automatically sizing and generating images for different users viewports.

The business end in your post, once you follow Bryce's [instructions](https://www.brycewray.com/posts/2021/04/using-eleventys-official-image-plugin/), ends up being a line in your post's markdown.

The word `image` here calls the method for processing that image.

## Styling

To stay focused, I publicly pledge to not waste time styling this until October 1, 2021.
