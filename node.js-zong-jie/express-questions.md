# express questions

## What is Express.js

Express is a minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications.

#### What type of web application can built using Express.js? <a id="what-type-of-web-application-can-built-using-expressjs"></a>

you can build single-page, multi-page, and hybrid web applications, as well as RestFUL APIs.

#### What are core features of Express framework? <a id="what-are-core-features-of-express-framework"></a>

* It allows middleware set up to respond HTTP Requests
* It defines routing table which is used to achieve action based on HTTP Method and URL.
* It allows dynamically generate the HTML Pages based on passing arguments to the templates.
* It follows MVC architecture for web application.

#### What is middleware in Express.js? <a id="what-is-middleware-in-expressjs"></a>

Middleware is a function that accesses the request object \(req\), response object \(res\), and access next middleware function in application's request-response cycle. The next middleware function is represented by variable called 'next'.

#### What is 'next' in Express.js? <a id="what-is-next-in-expressjs"></a>

'next' is a parameter which is passed in middleware function to pass control to next middleware or handler.

#### What is routing? <a id="what-is-routing"></a>

Routing define how an application responds over client request to a particular endpoint \(URI\). Endpoint is specially a path and any one of HTTP request methods \(GET, POST, etc\).

```text
app.METHOD(PATH,HANDLER)
```

