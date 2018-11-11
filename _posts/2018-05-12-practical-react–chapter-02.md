---
layout: post
title: "Practical React – Chapter 2"
date: 2018-05-12
---

In our previous tutorial, [Practical React – Chapter 1](https://ehsankorhani.com/blog/2018/04/29/practical-react–chapter-01), we set up a simple environment to render React component to our page.
In that post, we used `React.createElement()` function, but that is too verbose. React has another solution for you.

### JSX
Is a simple way to create HTML like views that will render to real HTML DOM (or other data representation environments such as Mobile or PDF). The language itself is very simple, so we try to learn it alongside our React tutorial journey.

Something we should note is that browsers do not understand JSX. Therefore, another tool is needed to transform it to React.createElement().
<!--more-->
### Setting up [Babel](https://babeljs.io/)
It’s not just the JSX. The browsers do not understand many aspects of modern JavaScript as well. ES6 and other new versions of JavaScript are not yet fully implemented in the browsers.

Therefore, Babel will come handly a lot in transpiling new React syntax to old ES5.

To use Babel we need to install _babel-cli_ it globally through a package manager:

```bash
npm install -g babel-cli
```

Initiate a project to add _package.json_ to your project:

```bash
npm init
```

And, install Babel preset for React.

```bash
npm install babel-preset-react --save-dev
npm install babel-preset-env --save-dev
```

Presets are a group of plugins. Read about them at http://babeljs.io/docs/plugins.

### Let’s write JSX
Our machine is now ready and knows how to compile JSX.

At the root of your project create a new folder and call it “src”. This will be the input for your application and a place for plain React code.
We also need an output for our browser. So, create another folder and name it “public”.

Add a new file to the “src” folder and call it “app.js”. Write the following inside your new file:

```javascript
var template = <p>Hello React with JSX!</p>;

var appRoot = document.getElementById("app");

ReactDOM.render(template, appRoot);
```

Modify your _index.html_ so it gets its _app.js_ file from:

```html
<script src="./public/app.js"></script>
```

Now run Babel in command prompt:

```bash
babel src/app.js --out-file=public/app.js --presets=react,env
```

Your transformed react file is ready inside public folder. Just like the one you wrote before.


### Watch for changes

For any change you make to your src/app.js file, you have to run the babel command again. To avoid that just add a

```bash
-- watch
```

at the end of your command and it will compile you _src/app.js_ to _public/app.js_ on any file save.
