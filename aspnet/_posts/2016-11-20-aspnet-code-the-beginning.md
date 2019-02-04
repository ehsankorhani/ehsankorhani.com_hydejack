---
layout: post
title: "ASP.NET Core – The Beginning"
date: 2016-11-20
author: ehsan
excerpt_separator: <!--more-->
---

ASP.NET Core is so much influenced by the way Node.js applications are created.
<!--more-->
Perhaps the biggest advantage of Core over its predecessor is that it is no longer relies on IIS web server. Like Node, Core communicates with a wrapper over web server as well. It’s the job of this wrapper (in Core case, Kestrel) to work with the underlying web server. Therefore, Core is not bound to a particular web server and is able to run on different platforms.

In addition, Core, uses json configuration files like Node. No more verbose XML config files.
