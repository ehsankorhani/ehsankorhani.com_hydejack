---
layout: post
title: "REST is stateless"
date: 2016-11-22
---

Web applications (over HTTP) are disconnected. This means that once the server sends data over the wire to the client it forgets about it. The client on the second call should remind the server of its state.
<!--more-->

<img class="img-align-right" src="/assets/images/explor2.jpg" alt="ASP.NET Session State">
Session state is a method to keep track of web application users. The server needs to store client data in some place and assign it to only that client. Therefore, it creates a unique id for every value for a single user, encrypts and return that back to the user. These encrypted data received back on later calls by the server. They were especially important in ASP.NET Web Forms for passing data between different pages.

### Server does not store data in REST architecture.

No more storing user data’s in session (which in fact could be anything) in REST applications. The client needs to keep whatever data it requires on its own machine and send them to the server if required.

If data was missed (by a browser refresh command, …) it has to request them again.

This doesn’t mean that the client should transmit sensitive or large data each time over the wire to the server. These kinds of data can be fetched from the persistent layer by a single key id. Caching is another solution the server can provide on frequently queried data.
