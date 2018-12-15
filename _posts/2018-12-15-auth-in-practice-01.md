---
layout: post
title: "Authentication and Authorization in Practice – Chapter 1"
date: 2018-12-15
---

Authentication and Authorization are an important concepts in any type of software development. Systems over network need a mechanism to allow or deny access to the protected resources.

In earlier days, _Basic_ or _Forms_ authentication approach were sufficient enough as the _Resource Owners_ (or Users) would directly want to access their own data on a remote server.

<!--more-->

#### Basic Authentication

<img src="/assets/images/security-httpBasicAuthentication.gif" alt="Diagram of four steps in HTTP basic authentication between client and server (docs.oracle.com)" />

It was simply the steps to:
1. Request a resource from a server
2. Being redirected to login page
3. Enter username and password

```bach
GET /login/ HTTP/1.1
Host: www.ehsankorhani.com
Authorization: Basic aAJ0cKfgdGCoObE=
```

4. Server will lookup user info
5. Get access to protected page.
..* Normally in the form of a Cookie
..* Browser will send this Cookie in each subsequent request
.. `Set-Cookie: id=a3fWa; Expires=Wed, 21 Oct 2015 07:28:00 GMT;`


The encrypted text in authorization header is just a:
`base64Encode(username:password)`

Providing basic authentication requires the back-end server to implement a user database with proper hashing and security measures.
[ASP.NET Identity](https://www.asp.net/identity) is one of the Microsoft technologies to simplify this task.


