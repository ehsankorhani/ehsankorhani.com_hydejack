---
layout: post
title: "Practical React – Chapter 1"
date: 2018-04-29
---

### Hello React
The simplest way to create a React app is by adding React scripts to an HTML page.

You need to include react.js and react-dom.js to page Header (use the minified version when deploying to the production environment):

```html
<script src="https://fb.me/react-0.14.3.js"></script>
<script src="https://fb.me/react-dom-0.14.3.js"></script>
```

Next, include your own app.js file at the bottom of your HTML page and before the **closing Body tag**.

```html
<script src="./scripts/app.js"></script>
```
<!--more-->
React needs to render to a DOM element. therefore, add an element with ID to your HTML, and you are good to go.

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <title>Page Title</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <script src="https://fb.me/react-0.14.3.js"></script>
    <script src="https://fb.me/react-dom-0.14.3.js"></script>
</head>
<body>
    <div id="app"></div>

    <!-- scripts -->
    <script src="./scripts/app.js"></script>
</body>
</html>
```

For the time being, because we are not going to use jQuery Ready function, we need to add our app.js file after all DOM elements to ensure they have been rendered inside the browser.

### Developing with React

Add the following code snippet to the app.js:

```javascript
var template = React.createElement (
    "h3",
    { id: "pageTitle" },
    "Hello React"
);
```

var appRoot = document.getElementById("app");

ReactDOM.render(template, appRoot);Copy
Your React app is ready.

Save and open your HTML page to see the result.

**Why so many lines of code to produce only a single HTML element?**

Well, rendering the DOM via React (line 9) happens only once per application.

*createElement*, on the other hand, is a function of React library that creates an HTML element based on the inputs.

React uses *JSX* to create the elements. However, browsers do not understand JSX and therefore, we need the *Babel* transpiler to convert JSX to JavaScript.

In future posts, we will explore Babel library in more details.

[https://github.com/ehsankorhani/PracticalReact/tree/master/Chapter-01](https://github.com/ehsankorhani/PracticalReact/tree/master/Chapter-01)
