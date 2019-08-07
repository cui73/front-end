# express

## Basic 

const express = require\('express'\)

const app = express\(\)  
Add a new route method to handle requests for the path "/". The first argument specifies the path or URL, the next argument is the route handler. Inside the route handler, let's use the response object to send a status code 200 \(OK\) and text to the client

app.get\('/', \(request, response, nextHandler\) =&gt; {

response.status\(200\).send\('Hello from ExpressJS'\)

}\)

Finally, use the listen method to accept new connections on port 1337:

app.listen\(1337, \(\) =&gt; console.log\('Web Server running on port 1337'\),\)



## Initial

create new 

```text
var express = require('express');
var app = express();

app.get('/', function(req, res){
  res.send('hello world');
});

app.listen(3000);
```



## Router :



We can use app.route\(\)

```text
app.route('/book')
  .get(function(req, res) {
    res.send('Get a random book');
  })
  .post(function(req, res) {
    res.send('Add a book');
  })
  .put(function(req, res) {
    res.send('Update the book');
  });
```



Routing refers to determining how an application responds to a client request to a particular endpoint, which is a URI \(or path\) and a specific HTTP request method \(GET, POST, and so on\).

```text
app.METHOD(PATH, HANDLER);
```

A `router` object is an isolated instance of middleware and routes. You can think of it as a “mini-application,” capable only of performing middleware and routing functions. Every Express application has a built-in app router

CRUD

```text
// GET method route
app.get('/', function (req, res) {
  res.send('GET request to the homepage');
});

// POST method route
app.post('/', function (req, res) {
  res.send('POST request to the homepage');
});
```

```text
app.put('/user', function(req, res) {
  res.send('Got a PUT request at /user');
});
```

```text
app.delete('/user', function(req, res) {
  res.send('Got a DELETE request at /user');
});
```

![](../.gitbook/assets/image%20%289%29.png)

![](../.gitbook/assets/image%20%2816%29.png)

![](../.gitbook/assets/image%20%2813%29.png)

![](../.gitbook/assets/image%20%2817%29.png)

Respond to all METHOD to the /user route:

```text
app.all('/user', function(req, res) {
  res.send('Got a request at /user');
});
```



```text
const express = require('express');
const router = express.Router();

// middleware that is specific to this router
router.use(function timeLog(req, res, next) {
  console.log('request for books - Time: ', Date.now());
  next();
});
// define the home page route
router.get('/', function(req, res) {
  res.send('Books home page');
});
// define the about route
router.get('/about', function(req, res) {
  res.send('About books');
});

module.exports = router;
```

## Advanced Routing <a id="express-advanced-routing"></a>

regular expression

* `[abc]` Matches either an a, b or c character
* `[a-z]` Matches any characters between a and z, including a and z.
* `.` Matches any character other than newline
* `\d` Matches any decimal digit. Equivalent to \[0-9\].
* `a?` Matches an `a` character or nothing.
* `a+` Matches one or more consecutive `a` characters.
* `a*` Matches zero or more consecutive `a` characters.

```text
app.get('/ab?cd', function(req, res) {
  res.send('ab?cd');
});
```

#### Routing Parameter <a id="routing-parameter"></a>

```text
Route path: /users/:userId/books/:bookId
Request URL: http://localhost:3000/users/34/books/8989
req.params: { "userId": "34", "bookId": "8989" }

app.get('/users/:userId/books/:bookId', function(req, res) {
  res.send(req.params);
});
```

#### Request Body <a id="request-body"></a>

```text
const app = require('express')();
const bodyParser = require('body-parser');

app.use(bodyParser.json()); // for parsing application/json

app.post('/users', function(req, res) {
  res.send(req.body);
});
```

## app.use\(\[path\], function\)\]

```text
var express = require('express');
var app = express();

// 一个简单的 logger
app.use(function(req, res, next){
  console.log('%s %s', req.method, req.url);
  next();
});

// 响应
app.use(function(req, res, next){
  res.send('Hello World');
});

app.listen(3000);
```

static:, ./public static service

```text
app.use(express.static(__dirname + '/public'));
```

## app.all\(path, \[callback...\], callback\)

match all HTTP active

## Handling error

In Express, 404 responses are not the result of an error, so the error-handler middleware will not capture them. This behavior is because a 404 response simply indicates the absence of additional work to do; in other words, Express has executed all middleware functions and routes, and found that none of them responded. All you need to do is add a middleware function at the very bottom of the stack \(below all other functions\) to handle a 404 response:

```text
app.use(function(req, res, next) {
  res.status(404).send("Sorry can't find that!");
});

app.use(function(err, req, res, next) {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```



## Express Middleware

1. app.use `app.METHOD()` 
2. router.use `router.METHOD()` 
3.  err app.use\(function\(err, req,res,next\)\)
4. import, third party middleware 

```text
router.use('url',function(req,res,next){next()})
```

```text
app.use('url', function(req,res,next){next()})
```

Middleware functions are functions that have access to the request object \(req\), the response object \(res\), and the next middleware function in the application’s request-response cycle. The next middleware function is commonly denoted by a variable named next.

* [应用层中间件](https://expressjs.com/zh-cn/guide/using-middleware.html#middleware.application)
* [路由器层中间件](https://expressjs.com/zh-cn/guide/using-middleware.html#middleware.router)
* [错误处理中间件](https://expressjs.com/zh-cn/guide/using-middleware.html#middleware.error-handling)
* [内置中间件](https://expressjs.com/zh-cn/guide/using-middleware.html#middleware.built-in)
* [第三方中间件](https://expressjs.com/zh-cn/guide/using-middleware.html#middleware.third-party)

Middleware functions can perform the following tasks:

* Execute any code.
* Make changes to the request and the response objects.
* End the request-response cycle.
* Call the next middleware function in the stack.

middleware e.g.

function: redirect\('/login'\);

```text
app.use(function(req, res, next) {
  if (req.isAuthenticated) {
    next();
  } else {
    res.redirect('/login');
  }
});
```

```text
// define the home page route
router.get('/', function(req, res) {
  res.send('Books home page');
});
```

**Example - Error Handling**

You define error-handling middleware in the same way as other middleware, except with four arguments instead of three; specifically with the signature \(err, req, res, next\):

```text
app.use(function(err, req, res, next) {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```

### third part :

```text
npm install cookie-parser

var cookieParser = require('cookie-parser');
// load the cookie-parsing middleware
app.use(cookieParser());
```

