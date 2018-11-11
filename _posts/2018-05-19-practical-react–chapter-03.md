---
layout: post
title: "Practical React – Chapter 3"
date: 2018-05-19
---

### An introduction to JSX
JSX or JavaScript XML is an HTML like language React uses to create the Component’s View. It’s pretty simple if you are already familiar with basic HTML with few caveats regarding JavaScript keywords.

For example, “class” is a keyword, and thus you will use “className” to refer to CSS inside your JSX.
<!--more-->
A sample basic JSX code would look like:

```javascript
const template = (
  <div>
    <h2>JSX Tutorial</h2>
    <div className="content-body">
      <label>Link to discussion:</label>
      <button onclick="redirect()"></button>
    </div>
  </div>
);
```

#### Single Root
Every JSX template should have only one single root. In the example above, you can see that a pair of “div” elements wraps the whole component. The adjacent “label” and “button” elements are also wrapped inside another div.

#### Expressions
JavaScript code and expressions can be interpolated inside a pair of Curly Brackets or `{ }`.

```javascript
const admin = {
  firstName: "Ehsan",
  lastName: "Korhani"
}

const element = (
  <div>
    <h2>JSX Tutorial</h2>
    <div className="content-body">
      <p>Author: {admin.firstName} {admin.lastName.toUpperCase()}</p>
      <div>{new Date().getFullYear()}</div>
    </div>
  </div>
);
```

#### Conditional Rendering
Conditional rendering in JSX allows React to render a piece of view based on a condition.

_Short-Circuiting_ is a feature in JavaScript that makes a statement evaluate to its last evaluated operator. So, for the `||` operator the first Truthy value will be returned and `&&` will return its last Truthy value.
Therefore;

```javascript
0 || "JSX" || true === "JSX"
1 && "JSX" && true === true
```

By knowing this we can use `&&` operator to render a piece of JSX code conditionally.

```javascript
const curentYear = new Date().getFullYear();

const element = (
  <div>
    <h2>JSX Tutorial</h2>
    <div className="content-body">
      <p>Author: {admin.firstName} {admin.lastName.toUpperCase()}</p>
      {curentYear >= 2018 && <div>{curentYear}</div>}
    </div>
  </div>
);
```

Ternary Operator can be used in case you need an alternative response when the evaluation was false.

```javascript
{(curentYear >= 2018) ? <div>{curentYear}</div> : "old post"}
```

And for even more complex cases, a function can be defined to be used inside JSX template.

```javascript
const getFullName = (person) => {
  if (person.firstName && person.lastName) {
    return person.firstName + " " + person.lastName;
  } else {
    return "Anonymous";
  }
}

<p>Author: {getFullName(admin)}</p>
```
