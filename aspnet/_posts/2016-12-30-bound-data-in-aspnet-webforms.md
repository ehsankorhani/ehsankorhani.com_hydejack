---
layout: post
title: "Altering bound data in ASP.NET WebForms on client side"
date: 2016-12-30
author: ehsan
excerpt_separator: <!--more-->
---

Now this might seem a little bit old, but it was an issue I faced a while ago when I was working on an existing code. You might encounter that when working with legacy WebForm application as well.
<!--more-->
Modifying data – such as grid or dropdownlist values – on client-side is what we do every day by using JavaScript/jQuery or one of the JS frameworks. However, ASP.NET WebForm would not allow you to the same and modify it’s web controls data (which have been populated with data on the server).
This is for security reason.

However, you can achieve your task only by setting:

```html
<%@ Page ... EnableEventValidation="false" />
```

at top of your aspx page.

**Warning!**
This is not a recommended action. As I mentioned, it will cause security issues.

It’s just a workaround in case you are pretty sure about the security of environment your application is running in.
