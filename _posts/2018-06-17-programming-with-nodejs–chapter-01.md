---
layout: post
title: "Programming with Node.js – Chapter 1"
date: 2018-06-17
---

For a very long time we could run JavaScript code running on our machine through our browsers. Each vendor had its browser shipped with a specific JavaScript engine. Microsoft Edge has Chakra, Firefox uses SpiderMonkey, and Chrome was powered by V8.

Node community took V8 engine to build their runtime outside of browsers. So, developers can compile their JavaScript code to machine native code.
<!--more-->

### The benefits of Node.js
The foremost benefit was that it opens a whole new possibility to run the powerful, beautiful and familiar JavaScript in almost every platform and environment. Web developers could not use only a single programming language and JSON data format to build their applications on the server-side, client-side and on the database platforms.

Node is by nature a non-blocking, asynchronous application. In comparison, C# is a blocking language, unless you use its asynchronous features.

### Installing Node on your machine
On your favourite browser, navigate to nodejs.org. Download the LTS release and install it on your machine.
Open up your command prompt application and type the following commands:

```bash
node –v
npm -v
```

these should print the versions of Node and NPM installed on your machine.

### Hello Node!
Create a “.js” file and type the following and save the file:

```javascript
const tech = "Hello Node.js!!!";

console.log(tech);
```

In your command prompt browse to the path containing this file and type:

```bash
node app.js
```

This will print your defined variable in the console.

That was easy. But it’s just the beginning.

### vs. browser version
When using JavaScript in a browser you have access to some API’s provided by the browser, but that would be different outside.

For example, there is no DOM element anymore, so there won’t be a `document` variable. `window` global variable is replaced by `global`. And there is another global variable called `process`.

https://github.com/ehsankorhani/ProgrammingWithNode/tree/master/chapter-01
