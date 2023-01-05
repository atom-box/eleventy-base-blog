---
title: HTML and CSS snippets
description:
date: 2020-10-17
tags:
  - javascript
layout: layouts/post.njk
---

## Centering something vertically and horizontally

Without Flexbox or Grid.

```html
<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  position: relative;
  height: 400px;
  border: 2px solid #006100;
}

.centered-element {
  margin: 0;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}


</style>
<div class="container">
    <div class="centered-element">
      <p>As a sentence I consider myself doubly centered</p>
    </div>
</div>

```