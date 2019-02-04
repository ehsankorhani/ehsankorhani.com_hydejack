---
layout: post
title: "It’s important to avoid CSS !important"
date: 2016-11-15
author: ehsan
excerpt_separator: <!--more-->
---

I read this great article about [calculating CSS specificity](https://css-tricks.com/specifics-on-css-specificity/) value:

> * If the element has inline styling, that automatically1 wins (1,0,0,0 points)
> * For each ID value, apply 0,1,0,0 points
> * For each class value (or pseudo-class or attribute selector), apply 0,0,1,0 points
> * For each element reference, apply 0,0,0,1 point
<!--more-->
This is how should we go about giving specificity to our CSS codes.

Try not to use !important as it breaks the above rule and makes it difficult to maintain and modify existing CSS codes.
