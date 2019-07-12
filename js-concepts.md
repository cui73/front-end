# JS Concepts

## 1.**Explain event delegation**

Event delegation is a technique involving adding event listeners to a parent element instead of adding them to the descendant elements. The listener will fire whenever the event is triggered on the descendant elements due to event bubbling up the DOM. The benefits of this technique are:

* Memory footprint goes down because only one single handler is needed on the parent element, rather than having to attach event handlers on each descendant.
* There is no need to unbind the handler from elements that are removed and to bind the event for new elements

## **2. Explain how `this` works in JavaScript**

There's no simple explanation for `this`; it is one of the most confusing concepts in JavaScript. A hand-wavey explanation is that the value of `this` depends on how the function is called. I have read many explanations on `this`online, and I found [Arnav Aggrawal](https://medium.com/@arnav_aggarwal)'s explanation to be the clearest. The following rules are applied:

1. If the `new` keyword is used when calling the function, `this` inside the function is a brand new object.
2. If `apply`, `call`, or `bind` are used to call/create a function, `this` inside the function is the object that is passed in as the argument.
3. If a function is called as a method, such as `obj.method()` — `this` is the object that the function is a property of.
4. If a function is invoked as a free function invocation, meaning it was invoked without any of the conditions present above, `this` is the global object. In a browser, it is the `window` object. If in strict mode \(`'use strict'`\), `this`will be `undefined` instead of the global object.
5. If multiple of the above rules apply, the rule that is higher wins and will set the `this` value.
6. If the function is an ES2015 arrow function, it ignores all the rules above and receives the `this` value of its surrounding scope at the time it is created.

## 3.Explain how prototypal inheritance works

This is an extremely common JavaScript interview question. All JavaScript objects have a `prototype` property, that is a reference to another object. When a property is accessed on an object and if the property is not found on that object, the JavaScript engine looks at the object's `prototype`, and the `prototype`'s `prototype` and so on, until it finds the property defined on one of the `prototype`s or until it reaches the end of the prototype chain. This behavior simulates classical inheritance, but it is really more of [delegation than inheritance](https://davidwalsh.name/javascript-objects).

## **4.promise vs observables**

**Promise** is always resolved with the first value passed to the resolve function and ignores further calls to it:

```javascript

  const numberPromise = new Promise((resolve) => {
    resolve(5);
    resolve(10);
});

numberPromise.then(value => console.log(value));
// still prints only 5
```

**Observables** allow you to resolve \(or, as we say, “emit”\) multiple values

```javascript
const numberObservable = new Observable((observer) => {
    observer.next(5);
    observer.next(10);
});

numberObservable.subscribe(value => console.log(value));
// prints 5 and 10
```

## **5. typeof null ==**  Object

## **6.local data storage?**

```javascript
// store data
localStorage.setItem('username', 'Andrew')

// get data
const name = localStorage.get('username')
console.log(name)

localStorage.removeItem('username')
localStorage.clear()
```

## **7.callback hell?**

Callback Hell, also known as Pyramid of Doom, is an anti-pattern seen in code of programmers who are not wise in the ways of asynchronous programming. It consists of multiple nested callbacks which makes code hard to read and debug. It is understandable how one might unknowingly get caught in Callback Hell while dealing with asynchronous logic.

using promise to fix it : Flattened callbacks Return values from asynchronous function Throw and Catch exceptions

## **8.What is the prototype?**

Prototypes are the mechanism by which JavaScript objects inherit features from one another. JavaScript is often described as a prototype-based language — to provide inheritance, objects can have a prototype object, which acts as a template object that it inherits methods and properties from. An object's prototype object may also have a prototype object, which it inherits methods and properties from, and so on. This is often referred to as a prototype chain, and explains why different objects have properties and methods defined on other objects available to them.

## **9. js data type**

**number** for numbers of any kind: integer or floating-point.

**string** for strings. A string may have one or more characters, there’s no separate single-character type.

**boolean** for true/false. 

**null** for unknown values – a standalone type that has a single value null. 

**undefined** for unassigned values – a standalone type that has a single value undefined. 

**object** for more complex data structures. 

**symbol** for unique identifiers.

## **10.how to store data in local storage**

```text
// store data
localStorage.setItem('username', 'Andrew')

// get data
const name = localStorage.get('username')
console.log(name)

localStorage.removeItem('username')
localStorage.clear()
```

## **11.new in es6**

```text
  Default Parameters in ES6
      var link = function(height = 50, color = 'red', url = 'http://azat.co') {
  ...
}

    Template Literals in ES6
      var name = `Your name is ${first} ${last}.`
      var url = `http://localhost:3000/api/messages/${id}`
    
    Multi-line Strings in ES6

      var roadPoem = `Then took the other, as just as fair,
    And having perhaps the better claim
    Because it was grassy and wanted wear,
    Though as for that the passing there
    Had worn them really about the same,`

     Destructuring Assignment in ES6

     Enhanced Object Literals in ES6

     Arrow Functions in ES6

     Promises in ES6

     Block-Scoped Constructs Let and Const

     classes in ES6
      
     modules in es6 (export=, import)
```

## **12.Right click function**

```text
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<button id = "btn1">点击我右击</button>
	<script type="text/javascript">
		//这一步是为了阻止右击时系统默认的弹出框
		document.getElementById("btn1").oncontextmenu = function(e){
	        e.preventDefault();
	    };
	    //在这里你就可以自己定义事件的函数啦
		document.getElementById("btn1").onmouseup=function(oEvent) {
		    if (!oEvent) oEvent=window.event;
		    if (oEvent.button==2) {
		        console.log('鼠标右击了')
		    }
		}
	</script>
</body>
</html>
--------------------- 
作者：三哥玩前端 
来源：CSDN 
原文：https://blog.csdn.net/zhaoxiang66/article/details/78063015 
版权声明：本文为博主原创文章，转载请附上博文链接！
```

## **13.the usage of Webpack**

Webpack is a tool wherein you use a **configuration to explain** to the builder **how to load specific things**. You describe to Webpack how to load`*.js` files, or how it should look at `.scss` files, etc. Then, when you run it, it goes into your entry point and walks up and down your program and figures out **exactly** what it needs, in what order it needs it, and what each piece depends on. It will then create **bundles** — as few as possible, as optimized as possible, that you include as the scripts in your application.

## **14.The pros of React and difference with Angular**

the pros of React: 

**reusability**: component can be repeated across several web pages

**virtual dom**: Through React’s memory reconciliation algorithm, the library constructs a representation of the page in a virtual memory, where it performs the necessary updates before rendering the final web-page into the browser. 

**One-direction**: data flow in ReactJS provides a stable code

**An open-source Facebook library**: constantly developing and open to the community

Wide **React and Redux toolset**

**------------------------------------------------------------------------------------------------------**

The differences with Angular:

#### **Data Binding:**

Angular allows two-way data binding while React allows one-way data binding.

Two-way data binding means that any changes you make to the model affect the view, and vice versa.

One-way data binding means any changes you make to the model affect the view, but not the other way around. This way, the data only flows in one direction.

#### **DOM Usage:**

Angular uses the browser's DOM, while React uses a virtual DOM.

A virtual DOM is a simplified version of the DOM. By using a virtual DOM, you can change any element very quickly and without needing to render the whole DOM. It drastically changes the performance from good to excellent.Using the virtual DOM is quite the buzz nowadays because it is faster, and speed is key!

#### **Language:**

Angularis a JS framework by nature, but is built to use TypeScript. React, on the other hand, is a JavaScript library as well, but recommends using JSX.

#### **Learning Curve:**

On average, TypeScript is considered harder to learn than JSX, in turn increasing the learning curve with Angular as compared to React.

#### **App Structure:**

Angular is a fully-featured MVC framework. React is just more of a 'V' in the MVC.

## **15.What is the prototype?**

Prototypes are the mechanism by which JavaScript objects inherit features from one another. JavaScript is often described as a prototype-based language — to provide inheritance, objects can have a prototype object, which acts as a template object that it inherits methods and properties from. An object's prototype object may also have a prototype object, which it inherits methods and properties from, and so on. This is often referred to as a prototype chain, and explains why different objects have properties and methods defined on other objects available to them.

## **16.How do you implement object-oriented programming in js?**

\*\*\*\*

## **17.How do you detect memory leak in js?**

```text
https://stackoverflow.com/questions/15970525/how-to-find-js-memory-leaks
```

**18.How to do async calls in js?**

a.XHR object method

b.callback function

c.es6 promise

d.es7 Async/await

\*\*\*\*

## **19.Call back hell 如何解决**

**Callback hell** is a phenomenon that afflicts a JavaScript developer when he tries to execute multiple asynchronous operations one after the other.

we can use Promises to solve this issue by :

**Flattened callbacks** 

**Return values from asynchronous function** 

**Throw and Catch exceptions**



##  20.**how to get Asyn restult in Backend?**



\*\*\*\*

## **21.array operation**

\*\*\*\*

**Create an Array**

```text
var fruits = ['Apple', 'Banana'];

console.log(fruits.length);
// 2
```

**Access \(index into\) an Array item**

```text
var first = fruits[0];
// Apple

var last = fruits[fruits.length - 1];
// Banana
```

**Loop over an Array**

```text
fruits.forEach(function(item, index, array) {
  console.log(item, index);
});
// Apple 0
// Banana 1
```

**Add to the end of an Array**

```text
var newLength = fruits.push('Orange');
// ["Apple", "Banana", "Orange"]
```

**Remove from the end of an Array**

```text
var last = fruits.pop(); // remove Orange (from the end)
// ["Apple", "Banana"];
```

**Remove from the front of an Array**

```text
var first = fruits.shift(); // remove Apple from the front
// ["Banana"];
```

**Add to the front of an Array**

```text
var newLength = fruits.unshift('Strawberry') // add to the front
// ["Strawberry", "Banana"];
```

**Find the index of an item in the Array**

```text
fruits.push('Mango');
// ["Strawberry", "Banana", "Mango"]

var pos = fruits.indexOf('Banana');
// 1
```

**Remove an item by index position**

```text
var removedItem = fruits.splice(pos, 1); // this is how to remove an item
                                        
// ["Strawberry", "Mango"]
```

**Remove items from an index position**

```text
var vegetables = ['Cabbage', 'Turnip', 'Radish', 'Carrot'];
console.log(vegetables); 
// ["Cabbage", "Turnip", "Radish", "Carrot"]

var pos = 1, n = 2;

var removedItems = vegetables.splice(pos, n); 
// this is how to remove items, n defines the number of items to be removed,
// from that position(pos) onward to the end of array.

console.log(vegetables); 
// ["Cabbage", "Carrot"] (the original array is changed)

console.log(removedItems); 
// ["Turnip", "Radish"]
```

**Copy an Array**

```text
var shallowCopy = fruits.slice(); // this is how to make a copy
// ["Strawberry", "Mango"]
```

\*\*\*\*

## **22.**what are promise, promise chain!!!!!!!!!!! promise.all?

**promise**_:The_ Promise object represents the eventual completion \(or failure\) of an asynchronous operation, and its resulting value.

**promise state**: pending: initial state, neither fulfilled nor rejected. fulfilled: meaning that the operation completed successfully. rejected: meaning that the operation failed.

// creating a promise

```text
 const myPromise = new Promise ((resolve, reject) => {
   setTimeout( () => {
     resolve('Example data')
   }, 2000)
 })
```

// working with a Promise \(you can run some code when the promise is fulfilled or rejected by calling then on the promise\)

```text
 myPromise.then((data) => {
   console.log(data) // will print "Example data"
 }, (err) => {
      console.log(err)
 })
```

**promise chaining**: Promise chaining makes it easy to link together multiple promises and do one thing after something else has finished.

// define a promise and return a num \* 2

```text
 const getDataPromise = (num) => new Promise((resolve, reject) => {
   setTimeout( () => {
    typeof num === 'number' ? resolve(num * 2) : reject ('Number must be provided')
   }, 2000)
 })
```

//promise chaining

```text
 getDataPromise(10).then((data) => {
    return getDataPromise(data);
 }).then((data) => {
      console.log(data) // will print "40"
 }).catch((err) => {
      console.log(err)
 })
```

// fetch API return value from fetch is a promise and the promise gets resolved with response

```text
  fetch('http://puzzle.mead.io/puzzle', {}).then((response) => {
    if (response.status === 200) {
      return response.json() // jason method that returns a promise
    } else {
      throw new Error('Uable to fetch the puzzle')
    }
  }).then((data) => {
    console.log(data.puzzle)
  }).catch((error) => {
    console.log(error)
  })
```

// promise.all\(\)

```text
The Promise.all() method returns a single Promise that resolves when all of the promises passed as an iterable have resolved or when the iterable contains no promises. It rejects with the reason of the first promise that rejects.

  var promise1 = Promise.resolve(3);
  var promise2 = 42;
  var promise3 = new Promise(function(resolve, reject) {
    setTimeout(resolve, 100, 'foo');
  });

  Promise.all([promise1, promise2, promise3]).then(function(values) {
    console.log(values);
  });
  // expected output: Array [3, 42, "foo"]
```

## **23.When would you declare a variable with let as opposed to const?**

\*\*\*\*

Variables declared using the `var` keyword are scoped to the function in which they are created, or if created outside of any function, to the global object. `let` and `const` are _block scoped_, meaning they are only accessible within the nearest set of curly braces \(function, if-else block, or for-loop\).

```text
function foo() {
  // All variables are accessible within functions.
  var bar = 'bar';
  let baz = 'baz';
  const qux = 'qux';

  console.log(bar); // bar
  console.log(baz); // baz
  console.log(qux); // qux
}

console.log(bar); // ReferenceError: bar is not defined
console.log(baz); // ReferenceError: baz is not defined
console.log(qux); // ReferenceError: qux is not defined
```

```text
if (true) {
  var bar = 'bar';
  let baz = 'baz';
  const qux = 'qux';
}

// var declared variables are accessible anywhere in the function scope.
console.log(bar); // bar
// let and const defined variables are not accessible outside of the block they were defined in.
console.log(baz); // ReferenceError: baz is not defined
console.log(qux); // ReferenceError: qux is not defined
```

`var` allows variables to be hoisted, meaning they can be referenced in code before they are declared. `let` and `const`will not allow this, instead throwing an error.

```text
console.log(foo); // undefined

var foo = 'foo';

console.log(baz); // ReferenceError: can't access lexical declaration 'baz' before initialization

let baz = 'baz';

console.log(bar); // ReferenceError: can't access lexical declaration 'bar' before initialization

const bar = 'bar';
```

Redeclaring a variable with `var` will not throw an error, but 'let' and 'const' will.

```text
var foo = 'foo';
var foo = 'bar';
console.log(foo); // "bar"

let baz = 'baz';
let baz = 'qux'; // Uncaught SyntaxError: Identifier 'baz' has already been declared
```

`let` and `const` differ in that `let` allows reassigning the variable's value while `const` does not.

```text
// This is fine.
let foo = 'foo';
foo = 'bar';

// This causes an exception.
const baz = 'baz';
baz = 'qux';
```

## **24.What are some advantages of JSON \(Over XML\)?**

Less Verbose: JSON has a more compact style than XML, and it is often more readable. The lightweight approach of JSON can make significant improvements in RESTful APIs working with complex systems. 

Faster: The XML software parsing process can take a long time. One reason for this problem is the DOM manipulation libraries that require more memory to handle large XML files. JSON uses less data overall, so you reduce the cost and increase the parsing speed. 

Readable: The JSON structure is straightforward and readable. You have an easier time mapping to domain objects, no matter what programming language you're working with. Structure Matches the Data: JSON uses a map data structure rather than XML's tree. In some situations, key/value pairs can limit what you can do, but you get a predictable and easy-to-understand data model. 

Objects Align in Code: JSON objects and code objects match, which is beneficial when quickly creating domain objects in dynamic languages. 

JSON Limitations: The limitations in JSON actually end up being one of its biggest benefits. A common line of thought among developers is that XML comes out on top because it supports modeling more objects. However, JSON's limitations simplify the code, add predictability and increase readability.

RESTful APIs depend on easy, reliable and fast data exchanges. JSON fits the bill for each of these attributes, while XML is struggling to keep up. As more developers expand their API integration skills, the advantages of a simple data exchange become apparent.

\*\*\*\*

## **25.What is JSON?**

JSON stands for JavaScript Object Notation

JSON is a lightweight format for storing and transporting data

JSON is often used when data is sent from a server to a web page

JSON is "self-describing" and easy to understand

## **26.Can you briefly describe a closure?**

A closure is the combination of a function and the lexical environment within which that function was declared. The word "lexical" refers to the fact that lexical scoping uses the location where a variable is declared within the source code to determine where that variable is available. Closures are functions that have access to the outer \(enclosing\) function's variables—scope chain even after the outer function has returned.

## **27.What JavaScript libraries and frameworks have you worked with?**

\*\*\*\*

## **28.What is a regular expression/RegExp?**

A regular expression is a special text string for describing a search pattern. You can think of regular expressions as wildcards on steroids. You are probably familiar with wildcard notations such as _.txt to find all text files in a file manager. The regex equivalent is ._.txt.

\*\*\*\*

## **29.Which keyword allows you to remove a member from an object?** 

**delete**

## **30.怎么debug JavaScript code，用什么工具debug** 

* React and Redux
  * [React Devtools](https://github.com/facebook/react-devtools)
  * [Redux Devtools](https://github.com/gaearon/redux-devtools)
* Vue
  * [Vue Devtools](https://github.com/vuejs/vue-devtools)
* JavaScript
  * [Chrome Devtools](https://hackernoon.com/twelve-fancy-chrome-devtools-tips-dc1e39d10d9d)
  * `debugger` statement
  * Good old `console.log` debugging

**我提到vscode有很多内置功能便于debug，对方不满意，最后他给我例子火狐浏览器怎么用break point 来debug**

## **31.闭包是什么，使用场景**

应用场景**:**

保护函数内的变量安全：如迭代器、生成器。

在内存中维持变量：如果缓存数据、柯里化。

**32.let / const / var 区别**

var: scope: it means where these variables are available for use var declaration are globally scoped or function/locally scoped. when a var declares outside of a function , it is globally scoped. so it is available for use in the whole window. if var declares within a function, it is available and can be accessed only within that function. var can be re-declared and updated. hoist: it is mechanism where avariables and function declarations can be moved to the top of their scope before code execution. bug: since you can redeclare of var, you would find that it is gonna be hard for you to debug.

let: scope: it is block scoped. let can be updated but not re-declared. However, if the same variable is defined in different sceopes, there will be no error. Just like var, let declarations are hoisted to the top. Unlike var which is initialized as undefined, the let keyword is not initialized. So if you try to use a let variable before declaration, you'll get a Reference Error.

const: Variables declared with the const maintain constant values. const declarations share some similarities with let declarations.Like let declarations, const declarations can only be accessed within the block it was declared. const cannot be updated or re-declared. Every const declaration therefore, must be initialized at the time of declaration. This behavior is somehow different when it comes to objects declared with const. While a const object cannot be updated, the properties of this objects can be updated hoist: Just like let, const declarations are hoisted to the top but are not initialized.

var declarations are globally scoped or function scoped while let and const are block scoped.

var variables can be updated and re-declared within its scope; let variables can be updated but not re-declared; const variables can neither be updated nor re-declared.

They are all hoisted to the top of their scope but while var ****variables are initialized with undefined, let and const variables are not initialized.

While var and let can be declared without being initialized, const must be initialized during declaration.

**33.解决reserved name 的dubug工具 //这个是什么？use strict吗？//ESLint**

\*\*\*\*

## **34.event-loop how it works**

The event loop is a single-threaded loop that monitors the call stack and checks if there is any work to be done in the task queue. If the call stack is empty and there are callback functions in the task queue, a function is dequeued and pushed onto the call stack to be executed.

**35.how to use export and import**

\*\*\*\*

### [Export before declarations](https://javascript.info/import-export#export-before-declarations)

We can label any declaration as exported by placing `export` before it, be it a variable, function or a class.

For instance, here all exports are valid

```text
      // export an array
export let months = ['Jan', 'Feb', 'Mar','Apr', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];

// export a constant
export const MODULES_BECAME_STANDARD_YEAR = 2015;

// export a class
export class User {
  constructor(name) {
    this.name = name;
  }
}
```



### [port apart from declarations](https://javascript.info/import-export#export-apart-from-declarations)

Also, we can put `export` separately.

Here we first declare, and then export:

```text

// 📁 say.js
function sayHi(user) {
  alert(`Hello, ${user}!`);
}

function sayBye(user) {
  alert(`Bye, ${user}!`);
}

export {sayHi, sayBye}; // a list of exported variables
```



### [Import \*](https://javascript.info/import-export#import)

Usually, we put a list of what to import into `import {...}`, like this:

```text


// 📁 main.js
import {sayHi, sayBye} from './say.js';

sayHi('John'); // Hello, John!
sayBye('John'); // Bye, John!
```

But if the list is long, we can import everything as an object using `import * as <obj>`, for instance:

```text


// 📁 main.js
import * as say from './say.js';

say.sayHi('John');
say.sayBye('John');
```



### [Import “as”](https://javascript.info/import-export#import-as)

We can also use `as` to import under different names.

For instance, let’s import `sayHi` into the local variable `hi` for brevity, and same for `sayBye`:

```text


// 📁 main.js
import {sayHi as hi, sayBye as bye} from './say.js';

hi('John'); // Hello, John!
bye('John'); // Bye, John!
```

### [Export “as”](https://javascript.info/import-export#export-as)

The similar syntax exists for `export`.

Let’s export functions as `hi` and `bye`:

```text
// 📁 say.js
...
export {sayHi as hi, sayBye as bye};
```

Now `hi` and `bye` are official names for outsiders:

```text
// 📁 main.js
import * as say from './say.js';

say.hi('John'); // Hello, John!
say.bye('John'); // Bye, John!
```

### [export default](https://javascript.info/import-export#export-default)

So far, we’ve seen how to import/export multiple things, optionally “as” other names.

In practice, modules contain either:

* A library, pack of functions, like `lib.js`.
* Or an entity, like `class User` is described in `user.js`, the whole module has only this class.

Mostly, the second approach is preferred, so that every “thing” resides in its own module.

Naturally, that requires a lot of files, as everything wants its own module, but that’s not a problem at all. Actually, code navigation becomes easier, if files are well-named and structured into folders.

Modules provide special `export default` syntax to make “one thing per module” way look better.

It requires following `export` and `import` statements:

1. Put `export default` before the “main export” of the module.
2. Call `import` without curly braces.

For instance, here `user.js` exports `class User`:

```text

              // 📁 user.js
export default class User { // just add "default"
  constructor(name) {
    this.name = name;
  }
}
```

…And `main.js` imports it:

```text

           // 📁 main.js
import User from './user.js'; // not {User}, just User

new User('John');
```

## **36.tell me about two ways for  inheritance**

\*\*\*\*

## **37. how to use fetch function?**

```text
fetch(url)
  .then(function(data) {
    // Here you get the data to modify as you please
    })
  })
  .catch(function(error) {
    // If there is any error you will catch them here
  });   
```

\*\*\*\*

## **38.what is the null process? how many process in our javascripts\(not single thread question, he means process with js\)**

A null process—which takes its name from the concept of null pointers—is what happens when no formal process is put in place.

\*\*\*\*

## **39.how to loop a object with multiple layer\(dfs,bfs\)different between dfs and bfs**

\*\*\*\*



## **40. this的用法**

已有

## **41.写一个debounce方程**

```text
// Returns a function, that, as long as it continues to be invoked, will not
// be triggered. The function will be called after it stops being called for
// N milliseconds. If `immediate` is passed, trigger the function on the
// leading edge, instead of the trailing.
function debounce(func, wait, immediate) {
	var timeout;
	return function() {
		var context = this, args = arguments;
		var later = function() {
			timeout = null;
			if (!immediate) func.apply(context, args);
		};
		var callNow = immediate && !timeout;
		clearTimeout(timeout);
		timeout = setTimeout(later, wait);
		if (callNow) func.apply(context, args);
	};
};
```

\*\*\*\*

## **42.手写map方法**

```text
Array.prototype.fakeMap = function fakeMap(fn, context) {
  if (typeof fn !== "function") {
    throw new TypeError(`${fn} is not a function`);
  }
  
  let arr = this;
  let temp = [];
  for (let i = 0; i < arr.length; i++) {
	// 迭代执行
    let result = fn.call(context, arr[i], i, arr);
    temp.push(result);
  }
  return temp;
};

检测：

let arr = ["x", "y", "z"];

arr.fakeMap((item, index, arr) => console.log(item, index, arr));
1
2
3
输出：

x 0 [ ‘x’, ‘y’, ‘z’ ]
y 1 [ ‘x’, ‘y’, ‘z’ ]
z 2 [ ‘x’, ‘y’, ‘z’ ]
--------------------- 
作者：Beijiyang999 
来源：CSDN 
原文：https://blog.csdn.net/beijiyang999/article/details/80179097 
版权声明：本文为博主原创文章，转载请附上博文链接！
```

\*\*\*\*

## **43.event loop**

已有

## **44.how to do the error handling:** 

## 45.**how to parse the json data type**

## **46.javascript validation**

## **47.cross browser compatibility issues**

## **48.how to judge input finished \(debounce\)**

## **49.call\(\), bind\(\), apply\(\)**

## **50. inheritance**

**51.typeof array**

**52.javascript design pattern**

**53.how to use Pure JavaScript to accomplish data binding method**

**54.explain different HTTP request methods**

**55.what is mixin**

56.**pros and cons of using mixin**

**57.explain how the mixin function like in your project**

**58.how to use JavaScript to write a dropdown list**

59.**setter and getter in javascript ?**

**60.how to deep copy and shallow copy an object**

**61. explain ES6 arrow function, why you prefer to use that**

**62.how to create a Class in javascript**

**63.how to make HTTP request security \(CDS, CORS\)**

**64.search bar的细节，怎么取得data//服务器用regux expression，怎么返回结果**

**65.怎么detele property（1.delete 2.prototype）**

**66. input bar怎么做，onchange = {this.handleChange}**

**67.**

1. **What is the difference between get and post?**
2. **what is the difference between post and put?**
3. **Do you know any other method other than get, put, post, delete?**
4. **How do you handle HTTP header?**

**68.Do you know different types of internet session?**

**69.http method why can’t use get function to create new one. GET vs POST**

**70.what’s functional programming tell some detail?**

**71.前端如何做security**

72. **What happened when you type in an url in a browser. 主要回答DNS, IP.**

**73.iife**

**74.经典的for循环里面加setTimeout， 问输出结果， 如何修改结果**

**75.Check if object is a array, use array.constructor === Array**

**76.difference between == and ===**

**77.difference between await and async**  


**78.**explain authentication

79.**什么是MVVM and 什么是MVC**

**80.pass by value and pass by reference**

**81. how do you import multiple functions from one module? give example \(让我白板上写几个case\) //用object**

**82.what design principle do you use mostly?**

**83.问我ES6的spread operator在ES5里面应该怎么写。**

**84.说几个javascript的design pattern，知道observer嘛，知不知道redux是observer的一种实现。**

**85.问SSR和CSR的区别，两个具问我HTML5 有些browser不支持，问我production的时候应该怎么做**

**86. what is promise and promise all; write a promise all if we have p1, p2, p3 几种 promise 写法**

**87.promise await**

88.**oop vs functional programming**

**89. js vs jquery**

**90. js vs java**

**91.strict mode**

**92.arraylist vs linkedlist**

**93.Where u put css file**

**Where u put js file**  


94.**One way data binding vs two way data binding**

**95. hoisting?**

96.**How to use bind call apply**

**97.Rest operator,.spread operator**

**98.difference between cookie, session storage, local storage**

**99.what is OAuth, do you do authentication in your project**

**100.Cross origin, cross domain**

**101.what is OAuth, do you do authentication in your project**

**102.Difference between null and undefined?  Which one is object**   


103.     **How to use closure/setTimeout/promise/async await/call apply bind**

**104.**

* **Null == undefined -&gt; true**
* **Null === undefined -&gt; false**

  
105.**Why we declare variable before function**

**106.Function with 4 arguments, what append if you put 3 arguments, and what is the forth argument**

**107.privileged method**

**108JavaScript build tools**

**109.What do you know about Next.js \(for server-side react application\)**

  


