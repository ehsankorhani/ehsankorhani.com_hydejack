---
layout: post
title: "Advanced JavaScript"
date: 2019-10-21
author: ehsan
excerpt_separator: <!--more-->
---

<img src="/assets/images/js-code-01.png" />

This article is going to discuss a more advanced topics of JavaScript language. This is journey to examine the different, wierd or specific features of JavaScript and also to practice the better ways to coding.

<!--more-->

##### Null vs Undefined
In many OOP languages such as C#, a variable cannot be declared without being initialized.
```csharp
/* C# */
var foo;  // compile error
var bar = null; // compile error
string baz = null; // ok
```

Here ```null``` is a "reference to a non-existing object" or a "null pointer".

However, this is completely possible in JavaScript.
If no value has been assigned to a variable, it will be have the ```undefined``` value.

```javascript
/* JS */
var foo;  // = undefined
var bar = undefined;  // = undefined
var baz = null;  // = null
```

In the above code, ```undefined``` means no value has been assigned, while ```null``` is just a special falsy value.

A best practice is to never assign ```undefined``` to a variable and use it to check if variable hasn't been initialized or assigned.

In addition while ```null``` is an _object_, ```undefined``` is of _undefined_ type.

```javascript
var nullType = typeof null;  // "object"
var undefinedType = typeof undefined;  // "undefined"
```

Keep in mind that while ```null``` is an (special) _object_, it evaluates as ```false```.

---

##### References

[The Modern JavaScript Tutorial](http://javascript.info/) <br />
[You Don't Know JS Yet (book series) - 2nd Edition](https://github.com/getify/You-Dont-Know-JS) <br />
[Eloquent JavaScript](http://eloquentjavascript.net/) <br />
[DOM Enlightenment](http://domenlightenment.com/) <br />
