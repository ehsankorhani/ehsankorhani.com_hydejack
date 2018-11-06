---
layout: post
title: "A Compass for your SASS"
date: 2017-01-05
---

Compass was a wonderful framework which unfortunately no longer is maintained. But the existing project can still be used by front-end developers.

### Twitter Bootstrap vs. Compass

Bootstrap is a CSS framework. It gives you a set of predefined styles. For instance, different types of Forms or Grids.
<!--more-->
On the other hand, [Compass](http://compass-style.org/) is a CSS authoring framework. It provides you with a collection of helpers or functions and it can help you create cleaner markup. You import compass to your SASS file by @import "compass"; and then you would be able to consume all its available functions, variables and mixins.

Alternatively you can import just the module you require: @import “compass/utilities”;

### How to use

Suppose you want to create a bullet list with an image instead of default symbol;

This is the module you should import at top of you SASS file:

```css
@import "compass/typography/lists/bullets";
```

Then:

```css
ul.pretty
+pretty-bullets("my-icon.png", 5px, 7px)
```

The above code will affect any ul decorated with class pretty.

### Spriting

Probably the best part of Compass is its power to convert you split images into Sprites.

Sprite is an image that contains smaller images which are then shown by CSS using the background-position property. Why we use it? Well, hitting server each time for a huge number of small images is not a good idea. It better to combine them together and get them from server in one request. But then, this is working best for images in small size.

Compass makes this approach a breeze.
Just put all your icons/images in a folder. Then import the appropriate module, directory and include them into SASS file:

```css
@import "compass/utilities/sprites";
@import "images/thumbs/*.png"; /* define root in config.rb */
@include all-thumbs-sprites;
```

Note that folder name should be similar to the middle word in @include command.
That’s it. Compass will generate the sprite and corresponding CSS code.

### How to use

You are now able to get width & height of any image/icon by its original name if you want to go the hard way and write your own CSS code:

```css
$width: thumbs-sprite-width($comming-soon-thumb);
$height: thumbs-sprite-height($comming-soon-thumb);
```

But by using Compass you only need to reference the image/icon by its name for any class:

```css
.any-class {
    @include thumbs-sprite(bicycle);
}
```
