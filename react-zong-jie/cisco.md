# Cisco

## 1.Interviewer asked me about my experience and technology skills I have worked on. They use bootstrap but I told them I have extensive knowledge of foundation 4 and both are similar and I will be able to pick up bootstrap easily. 

 I designed and built an one-page web application called employee management system from back end to the front for HR department. what this app does is to manage employees by allowing them to read, add, delete, update employees infos such as name, image, sms, address, and so on.  and also this app provides clear hierarchy views among employees , each employees can know who’s their manager.

For front end technologies, I used HTML5 , CSS3, BootStrap4 to build beautiful and responsive web page and React.js to create interactive UIs and Redux to manage states. For the back-end I used Node.js with Express framework to develop Restful API which ensures CRUD, and I also used mongoDB with mongoose functions for data storages, searching, sorting.

And the way how I make front-end talks to back-end is to use axios via get, post, put, delete methods.this project was deployed on AWS. I used GIT to do version control and collaboration with my colleagues. mocha for the testing

schema:

name, title, sex, startDate, officePhone, cellPhone, sms, email, manager, imageUrl 



work flows:

Github own branch

Use jest to test, and then push to my branch.

Other for CI/CD, use jenkins and pull my code, and build and deploy and test in Jenkins.

If there is problem, report to jira. And report this bug, then release new code and fix bug.

Github: version control.  Jenkins: CI/CD.  Jira: show the whole process and report bug.





## 2. Different JS frameworks and how they are different from one another.

| React | Angular |
| :--- | :--- |
| library | framework |
| JSX | typescript |
| one direction data-flow | bi-direction data-flow |
| one way data binding | two way data binding |
| component based | MVC, component based |

**Two-way** data binding means that any changes you make to the model affect the view, and vice versa.

**One-way** data binding means any changes you make to the model affect the view, but not the other way around. This way, the data only flows in one direction.

**MVC** works both in server and client side development. MVC architecture: the user updates the controller, the controller manipulates the model, the model updates the view, and finally the user can see the view.

**One-way direction** data flow is a pattern that works nicely with React. It is around the idea that the components do not modify the data that they receive. They only listen for changes of this data and maybe provide the new value but they do not update the actual data.

**bi-direction data-flow** 

\*\*\*\*

\*\*\*\*

\*\*\*\*

## **3.** Small discussion about JS promises.

* Promise represents the eventual completion of an async operation
* It must be in one of these states
  * pending
    * initial state, not fulfilled or rejected
  * fulfilled
    * meaning that the operation completed successfully
  * rejected
    * meaning that the operation failed
* It is guaranteed that a promise object will either succeed or fail
* promise.all 
  * returns a single promise that resolves when all of the promises in the argument have resolved or when the utterable argument contains no promises
* create Promise example

[`Promise.all(iterable)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)Wait for **all promises** to be resolved, or for any to be rejected. If the returned promise resolves, it is resolved with an aggregating array of the values from the resolved promises in the same order as defined in the iterable of multiple promises. I

[`Promise.race(iterable)`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/race) ``Wait until **any o**f the promises is resolved or rejected. If the returned promise resolves, it is resolved with the value of the first promise in the iterable that resolved. If it rejects, it is rejected with the reason from the **first promise** that was rejected.

[`Promise.reject(reason)`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/reject)

[`Promise.resolve(value)`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/resolve)Returns a new `Promise` object that is resolved with the given value. 

```javascript
function asyncDoubble(n) {
    return new Promise((resolve, reject) => {
        if (typeof n === "number") {
            resolve(n * 2);
        } else {
            reject(new Error (n + "is not a number!"));
        }
    });
}
asyncDouble(3).then(
    data => console.log(data);
    error => console.log(error);
);
```

promise chain

```text
new Promise(function(resolve, reject) {

  setTimeout(() => resolve(1), 1000); // (*)

}).then(function(result) { // (**)

  alert(result); // 1
  return result * 2;

}).then(function(result) { // (***)

  alert(result); // 2
  return result * 2;

}).then(function(result) {

  alert(result); // 4
  return result * 2;

});
```

## 4. Node.js what it is and how it's relevant to projects nowadays\(TBC\)

Node.js is an open-source server side runtime environment built on Chrome's V8 JavaScript engine which develop high performance web services. It also provides an event driven, non-blocking \(asynchronous\) I/O and cross-platform runtime environment for building highly scalable server-side application using JavaScript.

Benefits:

Good for beginner developers, JavaScript is simple to learn, rich framework \(Angular, Node, Backbone, Ember\)  one language rule all.

Module System: for packaging and namespacing code and to prevent name collisions

File System:  \(async with callbacks\)

fs.writeFile\(\)

fs.readFile\(\)

fs.writeFileSync\(\)

fs.readFileSync\(\)

fs.readir\(\)

use to create HTTP\(WEB\) SERVER\(easy use\)

Async I/O made easy

active community

multi-platform

Node.js is a JavaScript runtime that uses the V8 engine \(fast\)

real-time :Made Easy with Websockets



bad sides:

block on CPU\( CPU intensive tasks\)



## 5.Coding exercise on interviewers laptop on a UI wireframe they had. This was most of the interview as I had to design the whole page to be responsive using semantic HTML, vanilla JS and SCSS. Interviewers watched me while I was coding on the monitors and asked me about my coding style as to how I am structuring my code.

### write a nav bar 

```css
  /* Navbar Styling */
    .navbar {
      list-style: none;
      margin: 0;
      padding: 0;
      background: #4c6ca0;
      border-radius: 5px;
      overflow: auto;
    }

    .navbar li {
      float: left;
    }

    .navbar li a {
      display: block;
      color: #fff;
      text-decoration: none;
      padding: 15px 20px;
    }

    .navbar li a:hover {
      background-color: #446190;
      color: #f4f4f4;
    }
```

```markup
  <ul class="navbar">
    <li><a href="#">Home</a></li>
    <li><a href="#">About</a></li>
    <li><a href="#">Services</a></li>
    <li><a href="#">Contact</a></li>
  </ul>
  <br><br>
```

### Html

```markup
            // create a form
              <form id="task-form">
                <div class="input-field col s12">
                  <input type="text" name="task" id="task">
                  <label for="task">New Task</label>
                </div>
                <input type="submit" value="Add Task" class="btn">
              </form>
             
              // place where value show 
             <ul class="collection"></ul>
```

### 

### 

### hook up html and javascript

put &lt;script src="app.js"&gt; &lt;/script&gt;

```javascript
// Define UI Vars (hook class and id with javascript variables)
const form = document.querySelector('#task-form');
const taskList = document.querySelector('.collection');
const clearBtn = document.querySelector('.clear-tasks');
const filter = document.querySelector('#filter');
const taskInput = document.querySelector('#task');

// Load all event listeners
loadEventListeners();

// Load all event listeners
function loadEventListeners() {
  // DOM Load event
  document.addEventListener('DOMContentLoaded', getTasks);
  // Add task event
  form.addEventListener('submit', addTask);
  // Remove task event
  taskList.addEventListener('click', removeTask);
  // Clear task event
  clearBtn.addEventListener('click', clearTasks);
  // Filter tasks event
  filter.addEventListener('keyup', filterTasks);
}


// Add Task
function addTask(e) {
  if(taskInput.value === '') {
    alert('Add a task');
  }

  // Create li element
  const li = document.createElement('li');
  // Add class
  li.className = 'collection-item';
  // Create text node and append to li
  li.appendChild(document.createTextNode(taskInput.value));
  // Create new link element
  const link = document.createElement('a');
  // Add class
  link.className = 'delete-item secondary-content';
  // Add icon html
  link.innerHTML = '<i class="fa fa-remove"></i>';
  // Append the link to li
  li.appendChild(link);

  // Append li to ul
  taskList.appendChild(li);

  // Store in LS
  storeTaskInLocalStorage(taskInput.value);

  // Clear input
  taskInput.value = '';

  e.preventDefault();
}
```



## 6.Detailed discussion about SCSS and it's advantages and disadvantages.

The biggest difference SASS\(SCSS\) : the use of parentheses and semicolons.

SASS\(SCSS\) \(Syntactically Awesome Stylesheets\) is a CSS pre-processor that lets you use variables, mathematical operations, mixins, loops, functions, imports,Inheritances, and other interesting functionalities that make writing CSS much more powerful.

It's CSS syntax friendly\(what's available on css also available on Scss \)

It offers variables for whatever you want\(reuse later\)

It uses nested syntax \(More natural syntax and easy to read in most cases Prevents the need to rewrite selectors multiple times Better code organization and structure thanks to its visual hierarchy, which bring us to... More maintainable code\)

It includes mixins\(a mixin \(or mix-in\) is a class that contains methods for use by other classes without having to be the parent class of those other classes.\)

import rule. @import allows you to modularize your code making it easier to maintain by importing smaller SASS files. The difference between this and the CSS @import rule is that all imported SCSS files will be merged together into a single CSS file. you only do one http request.



## 7. Pseudo selectors in CSS and also asked me how I can improve my code and reuse the code.

A CSS pseudo-class is a keyword added to the end of a selector, preceded by a colon \(:\), which is used to specify that you want to style the selected element but only when it is in a certain state. For example, you might want to style a link element only when it is being hovered over by the mouse pointer, or a checkbox when it is disabled or checked, or an element that is the first child of its parent in the DOM tree.

:active :checked :default :dir :disabled :empty :enabled :first :first-child :first-of-type :fullscreen :focus :focus-within :hover :indeterminate :in-range :invalid :lang :last-child :last-of-type :left :link :matches\(\) :not :nth-child :nth-last-child :nth-last-of-type :nth-of-type :only-child :only-of-type :optional :out-of-range :read-only :read-write :required :right :root :scope :target :valid :visited



### how I can improve my code and reuse the code:

Keep the code DRY. Dry means "Don't Repeat Yourself". 

Make a class/method do just one thing. 

Write unit tests for your classes AND make it easy to test classes. 

Remove the business logic or main code away from any framework code Try to think more abstractly and use Interfaces and Abstract classes. 

Code for extension. Write code that can easily be extended in the future. Don't write code that isn't needed. Try to reduce coupling. Be more Modular



## 8. Performance related questions about best practices and how you can improve the pages performance.

### a . Clean up the HTML Document

put CSS at the top of your HTML document’s header in order to ensure progressive rendering.

Proper JavaScript Placement  placing JavaScript attributes at the bottom of your HTML

### b. Optimize CSS Performance

minimize bloated CSS files by using @import

### c. Reduce External HTTP Requests

eliminate any features that do not improve the experience of your visitors. These features may be: Unnecessary images Unnecessary JavaScript Excessive CSS Unnecessary plugins

### d. Minify CSS, JS and HTML



### e. Enable Prefetching

Prefetching can improve your visitors’ browsing experience by fetching necessary resources and related data before they are needed. There are 3 main types of prefetching:

Link Prefetching DNS Prefetching Prerendering With prefetching, the URL, CSS, images, and JavaScript are gathered for each link before you even leave your current webpage. This ensures that visitors can use links to navigate between pages with minimal loading times.

Fortunately, prefetching is easy to enable. Depending upon the type of prefetching you want to enable, you can simply add the rel="prefetch", rel="dns-prefetch", or rel="prerender" tag to your link attributes within your website’s HTML.

### f.Increase Speed With a CDN and Caching

You can significantly improve the speed and performance of your website by using a content delivery network. When you use a CDN, you link your website’s static content to an extended network of servers across the globe.

Properly setting up browser caching allows your browser to store certain files within its own cache to be delivered faster. Configuring this method can be done directly within your origin server’s configuration file.

### g. Compress Your Files

using Gzip

### h. Optimize Your Images

## 9 . Different CSS properties like position relative, absolute, z-index etc. And when to use one property over other.



* Static
  * This is the default value, all the elements are in order as they appear in the document
* Fixed \(always stay in the same place\)
  * The element is positioned relative to its normal position
  * This can be used to create a "floating" element that stays in the same position regardless of scrolling.
* Absolute
  * The element is positioned absolutely to its first positioned parent
  *  The absolutely positioned element is positioned relative to its _nearest positioned ancestor_ \(i.e., the nearest ancestor that is not `static`\).
* Relative \(line up form elements\)
  * The element is positioned related to the browser window
  * their normal position within the document
* Sticky
  * The element is positioned based on the user's scroll position
* The z-index\(Because the image has a z-index of -1, it will be placed behind the heading.\)

property specifies the stack order of an element. An element with greater stack order is always in front of an element with a lower stack order. z-index only works on positioned elements.



## 10.Box-sizing and the CSS box model

The box-sizing property defines how the width and height of an element are calculated: should they include padding and borders, or not.



box-sizing: border-box: Width and height apply to all parts of the element: content, padding and borders:All HTML elements can be considered as boxes. 

box-sizing: content-box \(default\): Width and height only apply to the content of the element



In CSS, the term box model is used when talking about design and layout. The CSS box model is essentially a box that wraps around every HTML element. It consists of margin, border, padding and context.



![](../.gitbook/assets/image%20%2814%29.png)

## 11. General web accessibility questions and user experience questions as to why in bootstrap a box is shown when it loads social share images as they seem broken when page loads.

* Use more semantic HTML
* Use correct headings
* Alternative text
* Declare the language and use clear language
* Write good links and link titles

## 12.CSS Grid vs Flex-box

a. CSS Grid Layout is a **two-dimensional** system, meaning it can handle both columns and rows, unlike flexbox which is largely a **one-dimensional system** \(either in a column or a row\).

b. A core difference between CSS Grid and Flexbox is that — CSS Grid’s approach is **layout-first** while Flexbox’ approach is **content-first**.   
_If you are well aware of your content before making layout, then blindly opt for Flexbox and if not, opt for CSS Grid._

c. Flexbox layout is most appropriate to the components of an application \(as most of them are fundamentally linear\), and **small-scale** layouts, while the Grid layout is intended for **larger scale** layouts which aren’t linear in their design.

d. If you only need to define a layout as a row or a column, then you probably need flexbox. If you want to define a grid and fit content into it in two dimensions — you need the grid.

## 13. Responsive Webpage Design

put this line of code &lt;link rel="stylesheet" href="css/main.css" /&gt;  into head

Below is important responsive code.

```css
@import 'variables';


body {
  font-family:$font-stack;
  background:$primary-color;
  color:white;
  text-align:center;
  padding-top: 100px;
}

h1 {
  display: none;
}

// smartphones
@media only screen and (max-width: 500px) {
  body {
    background:$smartphone-color;
  }

  #smartphone {
    h1 {
      display: block;
    }
  }
}

  // Tablet
  @media(min-width: 501px) and (max-width: 768px) {
    body {
      background: $tablet-color;
    }

    #tablet {
      h1 {
        display: block;
      }
    }
  }

  // Normal
  @media(min-width: 769px) and (max-width: 1200px) {
    body {
      background:$normal-color;
    }
    #normal {
      h1 {
        display:block;
      }
    }
  }

  // Widescreen
  @media(min-width: 1201px) {
    body {
      background:$widscreen-color;
    }

    #widescreen{
      h1 {
        display:block;
      }
    }

  }

  // Landscape
  @media(max-height: 500px) {
    body {
      background: landscape-color;
    }

    #landscape {
      h1 {
        display: block;
      }
    }
  }


```







