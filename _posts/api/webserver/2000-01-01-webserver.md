---
layout: post
title: Web Server Module
categories: api webserver
permalink: api/webserver/index.html
---

**Stability:** _EXPERIMENTAL_

**Introduced:** PhantomJS 1.4

Using an embedded web server module called [Mongoose](http://code.google.com/p/mongoose/), PhantomJS script can start a web server. This is intended for ease of communication between PhantomJS scripts and the outside world and is _not_ recommended for use as a general production server. There is currently a limit of **10** concurrent requests; any other requests will be queued up.

To start using, you must `require` a reference to the `webserver` module:

```js
var webserver = require('webserver');
var server = webserver.create();
server.linsten(4000 , function(request , response){
    response.setHeader('Content-Type', 'text/plain;charset=utf-8');
    response.statusCode = 200;
    response.write('request : \n\n' + JSON.stringify(request , null , 4));
    response.close();
});
console.log('Server running at http://127.0.0.1:4000/');
```
