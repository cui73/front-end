# Node.js 总结

## Node.js

Node.JS is an open-source, cross-platform JavaScript runtime environment that executes JavaScript code server-side.

core is async I/O

Use async I/O not multi thread

like search:  db.query\('SELECT \* from some\_table', function\(res\) { res.output\(\); }\);

callback as second parameter. async -&gt; event loop, solve the block

everything is event loop

![](../.gitbook/assets/image%20%285%29.png)

Usage: node \[options\] \[ -e script \| script.js \] \[arguments\] 

e.g.: node debug script.js \[arguments\]



## **Node.js file operation**

To include the File System module, use the `require()` method.

* Read files - `fs.readFile()`
* Create files - `fs.appendFile(), fs.open(), fs.writeFile()`
* Update files - `fs.appendFile(), fs.writeFile()`
* Delete files - `fs.unlink()`
* Rename files - `fs.rename()`
* Upload files

\*\*\*\*

## **For Backend, did you use RestFul? what is the edit process in Node?**

\*\*\*\*

## **what is callback what arguments in callback in node.js**

The `util` module is primarily designed to support the needs of Node.js' own internal APIs. However, many of the utilities are useful for application and module developers as well. It can be accessed using:

```text
const util = require('util');
```

```text
const util = require('util');

async function fn() {
  return 'hello world';
}
const callbackFunction = util.callbackify(fn);

callbackFunction((err, ret) => {
  if (err) throw err;
  console.log(ret);
});
```

## **node js优点**

## **what framework did you use to create REST API?** 

**7.express router how it works if you have multiple function with different method.**

**8.build the router in node js, use controller for different function, show me the endpoint in middleware**

9.                 **how to implement the RESTful API**  


10. **how to implement the backend to connect with Mongodb**

**11.what are view and index in MongoDB? how to use index?  
12.callback in nodejs**

**13.What version of node.js you work with?**

**14.Which version of JS you use in node.js, ES5 or ES6?**

**15.What do you know about dependency management in node.js?**

**16.Do you know npm?**

**17.How to import and export in node.js? \(difference in ES5 and ES6\)**

**18.What is buffer class in node.js?**

**19.Tell me about file system in node.js.**

**20.single core and single thread.**

**21.difference between Ajax and node.js**

**22.how to achieve search.   regex -- filter in backend, so how to achieve  Restful API**

**23.**

  **a.backend part是怎么样的,** 

  **b.how to handle large amount data in frontend --- infinite scroll --- how to do this offset in url**

**24.how to process json?**

**25.express.js**

**26. how does node.js handle  sync code**

**27.what is  difference between setImmdiate\(\) and process.nextTick**

**28.Tell me about stream \(stream module\)**

**29.how to make NodeJS multi-threaded**

**30.how to use express to pass multiple function into one route**

**31.build the router in nodejs, use controller for different function, show me the endpoint in middleware**

**32.**

**a.CTE**

**b.CROS**

**c.CRUD**

**d. SQL：Left join，inner join**

**33.Child thread in node.js**

**34. REPL in node.js**

**35. Write a unique guid number in node/express.js**

**36.**

**how to pagenation from front end and back end**

**37. node.js event loop**

**38.**

**白板写两句REST API, 我写了require express和getAll, 他问我require跟import有什么区别, 我说require是node.js里的, import是ES6里的, 如果写后端server一定要用require, 前端就可以用import了, 因为前端ES6会被自动compile成ES5\(感谢Harry和Ian同学一天前的科普, 比心~\), 然后我说代码syntax不能保证完全正确, 但大概是这个样子**

**39.if there are multiple stories/ levels ?\(Use mongoose find $in and regex...\)**

**40.get data from MongoDB.**

**41. what is middleware**

**42. 问react的前端是如何与后端连接的, 我自己是在前端用http-proxy-middleware这个模块， 然后写setupProxy.js文件来修改前端发出请求的domain, 这样就能联系前后端，避免cors issue**

**43.mongoose是什么 为什么mongoose**

**44.如何建立一个express js application**

**45.如果express aplication 要增加route 怎么搞**

**46.how to use router of backend and frontend**

**47. use express to get id in a url**

**48.what is RESTful api**

49.**your project single thread or multi thread\(js is single thread\)**

**50.**

**node js 如何解决异步问题，假设我一定要等前一步的结果才能进行后一步怎么办，我说用await, for block sync**

**51.ajax vs node js**

**52. design database and frontend , how to access the database more quickly, how to improve performance if schema grows big, if u cache, what is the size of cache. …..\(This is the problem and challeng they are working on\)**

**53.server side render,  client side render, embed render**

**54.display none vs visibility hidden difference**

**55.search bar的细节，怎么取得data//服务器用regex expression，怎么返回结果**

  


  
  
  


  
  




