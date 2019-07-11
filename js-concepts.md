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

## **10.how to store data in local storage**

## **11.new in es6**



## **12.Right click function**

**13.the usage of Webpack**

**14.The pros of React and difference with Angular**

**15.What is the prototype?**

**16.How do you implement object-oriented programming in js?**

**17.How do you detect memory leak in js?**

**18.How to do async calls in js?**

**19.Call back hell 如何解决**  
20.**how to get Asyn restult in Backend?**

**21.array operation**

**22.What is a Promise in JavaScript?**

**23.When would you declare a variable with let as opposed to const?**

**24.What are some advantages of JSON \(Over XML\)?**

**25.What is JSON?**

**26.Can you briefly describe a closure?**

**27.What JavaScript libraries and frameworks have you worked with?**

**28.What is a regular expression/RegExp?**

**29.Which keyword allows you to remove a member from an object? delete**

**30.怎么debug JavaScript code，用什么工具debug** 

**我提到vscode有很多内置功能便于debug，对方不满意，最后他给我例子火狐浏览器怎么用break point 来debug**

**31.闭包是什么，使用场景**

**32.let / const / var 区别**

**33.解决reserved name 的dubug工具 //这个是什么？use strict吗？//ESLint**

**34.event-loop how it works**

**35.how to use export and import**

**36.tell me about two ways for  inheritance**

**37. how to use fetch function?**

**38.what is the null process? how many process in our javascripts\(not single thread question, he means process with js\)**

**39.how to loop a object with multiple layer\(dfs,bfs\)different between dfs and bfs**  


**40. this的用法**

**41.写一个debounce方程**

**42.手写map方法**

**43.event loop**

**44.how to do the error handling:**  


45.**how to parse the json data type**

**46.javascript validation**

**47.cross browser compatibility issues**

**48.how to judge input finished \(debounce\)**

**49.call\(\), bind\(\), apply\(\)**

**50. inherience**

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

  


