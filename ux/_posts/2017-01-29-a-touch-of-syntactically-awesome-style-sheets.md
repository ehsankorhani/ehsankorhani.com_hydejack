---
layout: post
title: "A touch of Syntactically Awesome Style Sheets"
date: 2017-01-29
author: ehsan
excerpt_separator: <!--more-->
---

CSS is great.

It does many things we used to do in HTML. It even does some of the stuff we do in JavaScript.

But the problem with CSS is that it lacks the programming atmosphere. It doesn’t have variables, modules, operators, functions, inheritance, …

So, people invented Less, Stylus and Sass.
<!--more-->
<img src="/assets/images/sass-logo.png" alt="SASS Logo" />

Sass is a language to make large CSS well-organized, write fewer lines of codes and to help maintain those codes. For example, we might need to assign color *#2E5F90* to may elements in our html/css codes. Later we changed our mind and want those elements in *#1D8353*. What is the solution? Find and Replace All? Yeah, that’s one solution. But wouldn’t it better if we could have something like this:

```css
$borders-color: #2E5F90 ;

div.frame {
  border-color: $borders-color;
}
```

Sass features syntaxes are pretty straight forward. You can read and learn to work with [Sass](http://sass-lang.com/) on its own [website](http://sass-lang.com/guide).

However, Partials are one important aspect I want to emphasize on.

> A partial is simply a Sass file named with a leading underscore.
>
> This is a great way to modularize your CSS and help keep things easier to maintain.

Previously we had to create a main css file, which everyone in team shares for all the pages in an application. After all, we didn’t want to create many small files and make hundreds of server calls.

Now, with Sass you can have as many css (or sass) files as you want. You just have to put an underscore at the beginning of its file name (e.g. _welcome-page.scss, _login.scss). And then you would go and create that main.scss file and just add this files inside:

```css
@import "login";
@import "welcome-page";
```

Sass watch will transform and import all the partials and would create file: main.css

It’s awesome.
