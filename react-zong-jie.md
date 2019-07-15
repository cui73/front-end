# React 总结

## **1.The pros of React and difference with Angular**

the pros of React: 

**reusability**: component can be repeated across several web pages

**virtual dom**: Through React’s memory reconciliation algorithm, the library constructs a representation of the page in a virtual memory, where it performs the necessary updates before rendering the final web-page into the browser. 

**One-direction**: data flow in ReactJS provides a stable code

**An open-source Facebook library**: constantly developing and open to the community

Wide **React and Redux toolset**

It's easy to know how a component is rendered, you just need to look at the render function. JSX makes it easy to read the code of your components. 

It's also really easy to see the layout, or how components are plugged/combined with each other. You can render React on the server-side. This enables improves SEO and performance. It's easy to test. 

You can use React with any framework \(Backbone.js, Angular.js\) as it's only a view layer.

**------------------------------------------------------------------------------------------------------**

The differences with Angular:

**library vs framework:**

A software framework \(be it front-end or backend\) includes standardized, pre-written code, which makes the development of certain functionalities easier and faster. You have less freedom to code, as you have to code as the framework architecture dictates.

A library is a collection of functions and functionalities, which you can use to achieve a certain end. You have more freedom to design and construct the system when using a library, but that adds more responsibility on the coder to be able to use it efficiently and find the right library for the right job, because, for projects which need to grow over time and become more serious, this could become significantly riskier and more difficult to manage.

The most significant difference between a framework and a library is how they interact with your code.

Your code calls the library while the framework calls your code.

This is also known as Inversion of Control. The litmus test for detecting a framework is checking if it has the Inversion of Control.

\*\*\*\*

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



## **2.what is hoc and when to use**

A higher-order component \(HOC\) is an advanced technique in React for reusing component logic. HOCs are not part of the React API, per se. They are a pattern that emerges from React’s compositional nature.

A higher-order component is a function that takes a component and returns a new component, for the concept of resuable component.

#### High Order Component Pattern <a id="high-order-component-pattern"></a>

```text
import React, { Component } from 'react';

const higherOrderComponent = OldComponnet => {
  class NewComponent extends Component {
    render() {
      return <OldComponnet />;
    }
  }
  return NewComponent;
};
```



#### Basic Example - Localization <a id="basic-example---localization"></a>

In order to implement the localization in the application, we need to share some common data across all components.

```text
// hoc for localization strings
const withLocalization = OldComponent => {
  class NewComponent extends Component {
    render() {
      const template = {
        en: {
          hello: 'hello',
          bye: 'bye'
        },
        cn: {
          hello: '你好',
          bye: '再见'
        }
      };
      // get the language from this.props
      // use en by default
      const lang = this.props.lang || 'en';
      const localizationString = template[lang];
      return <OldComponent localizationString={localizationString} />;
    }
  }
  return NewComponent;
};

// use hoc for Text and Button

const WithLocalizationButton = withLocalization(Button);
const WithLocalizationText = withLocalization(Text);

// app component
class App extends Component {
  render() {
    return (
      <div>
        <WithLocalizationButton />
        <WithLocalizationText />
      </div>
    );
  }
}

// Text component
function Text(props) {
  return (
    <p>{props.localizationString ? props.localizationString.hello : ''}</p>
  );
}
// Button component
function Button(props) {
  return (
    <button>
      {props.localizationString ? props.localizationString.bye : ''}
    </button>
  );
}
```



## **3.react render function**

\*\*\*\*

  
The `render()` method is the only required method in a class component.

When called, it should examine `this.props` and `this.state` and return one of the following types:

* **React elements.** Typically created via [JSX](https://reactjs.org/docs/introducing-jsx.html). For example, `<div />` and `<MyComponent />` are React elements that instruct React to render a DOM node, or another user-defined component, respectively.
* **Arrays and fragments.** Let you return multiple elements from render. See the documentation on [fragments](https://reactjs.org/docs/fragments.html) for more details.
* **Portals**. Let you render children into a different DOM subtree. See the documentation on [portals](https://reactjs.org/docs/portals.html) for more details.
* **String and numbers.** These are rendered as text nodes in the DOM.
* **Booleans or `null`**. Render nothing. \(Mostly exists to support `return test && <Child />` pattern, where `test` is boolean.\)

The `render()` function should be pure, meaning that it does not modify component state, it returns the same result each time it’s invoked, and it does not directly interact with the browser.

If you need to interact with the browser, perform your work in `componentDidMount()` or the other lifecycle methods instead. Keeping `render()` pure makes components easier to think about.

> Note
>
> `render()` will not be invoked if [`shouldComponentUpdate()`](https://reactjs.org/docs/react-component.html#shouldcomponentupdate) returns false.

\*\*\*\*

## **4.**reactDomServer

The ReactDOMServer object enables you to render components to static markup. Typically, it’s used on a Node server:

**a.**

Render a React element to its initial HTML. React will return an HTML string. You can use this method to generate HTML on the server and send the markup down on the initial request for faster page loads and to allow search engines to crawl your pages for SEO purposes.

```text
ReactDOMServer.renderToString(element)

```

b.

Similar to [`renderToString`](https://reactjs.org/docs/react-dom-server.html#rendertostring), except this doesn’t create extra DOM attributes that React uses internally, such as `data-reactroot`. This is useful if you want to use React as a simple static page generator, as stripping away the extra attributes can save some bytes.

If you plan to use React on the client to make the markup interactive, do not use this method. Instead, use [`renderToString`](https://reactjs.org/docs/react-dom-server.html#rendertostring) on the server and [`ReactDOM.hydrate()`](https://reactjs.org/docs/react-dom.html#hydrate) on the client.

```text
ReactDOMServer.renderToStaticMarkup(element)

```

## 5.**what is state, setState**

**state:**

The state of a React component is a place to store data inside the component. It is similar to a Javascript Object, but it is immutable.

A component's state should be considered as private data. This data is not exposed to the component that makes use of it. It is private and fully controlled by the component. It is only seen on the inside of component definitions. You can think of state as an internal data-set which affects the rendering of components.

Only Class Component has state, functional Component does not.

**setState: help to change the state value**

**why we need this method?**

When you use `this.state.color = 'red';` you mutate the state, it will not trigger re-render.

`this.setState({color: 'red'})` will create a new state and assign it to `this.state` changing it in an immutable way, thus React will know it has changed and will re-render the component.

#### Three important principles of setting state <a id="three-important-principles-of-setting-state"></a>

* Do not **modify** state directly, use `setState()` instead. The only place you can assign value to `this.state` is in the constructor.
* `setState()` may be asynchronous.
* State updates are merged.

## **6.life cycle methods**

Each React component has several “lifecycle methods” that you can override to run code at particular times in the process. Methods _prefixed with will_ are called right before something happens, and methods _prefixed with did_ are called right after something happens.

Through lifecycle methods, we can then control what happens when each tiny section of your UI renders, updates, thinks about re-rendering, and then disappears entirely.

**constructor:**

  ****The constructor for a React component is called before it is mounted. When implementing the constructor for a React.Component subclass, you should call super\(props\) before any other statement. Otherwise, this.props will be undefined in the constructor, which can lead to bugs.

**componentDidMount\(\):**

  ****componentDidMount\(\) is invoked immediately after a component is mounted.

**shouldComponentUpdate\(nextProps, nextState\):**

shouldComponentUpdate\(\) is invoked before rendering when new props or state are being received. Defaults to true. Use shouldComponentUpdate\(\) to let React know if a component’s output is not affected by the current change in state or props.

Use `shouldComponentUpdate()` to let React know if a component’s output is not affected by the current change in state or props. The default behavior is to re-render on every state change, and in the vast majority of cases you should rely on the default behavior.

**componentDidUpdate\(prevProps, prevState\):**

  ****componentDidUpdate\(\) is invoked immediately after updating occurs.

**componentWillUnmonut\(\):**

  ****componentWillUnmount\(\) is invoked immediately before a component is unmounted and destroyed.

```text
import React from "react";
import ReactDOM from "react-dom";
import { Component } from 'react';


import "./styles.css";

class App extends Component {
  constructor(props) {
    console.log('constructor called.');
    super(props);
    this.state = {number: 1};
  }

  componentDidMount() {
    console.log('componentDidMount() called.');
  }

  shouldComponentUpdate(nextProps, nextState) {
    console.log('shouldComponentUpdate() called.');
    console.log('current props: ', this.props);
    console.log('next props: ', nextProps);
    console.log('current state: ', this.state);
    console.log('next state: ', nextState);
    return true;
  }

  componentDidUpdate(prevProps, prevState) {
    console.log('componentDidUpdate() called.');
    console.log('current props: ', this.props);
    console.log('previous props: ', prevProps);
    console.log('current state: ', this.state);
    console.log('previous state: ', prevState);
  }
  componentWillUnmonut() {
    console.log('componentWillUnmonut() called.');
  }
  addOne = () => {
    this.setState({number: this.state.number + 1});
  };
  render() {
    console.log('render() called.');
    return (
      <div>
        <p>{this.state.number}</p>
        <button onClick={this.addOne}>Add One</button>
      </div>
    );
  }
}

const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);

```



\*\*\*\*

_\*\*\*\*_

## **7. life cycle 的顺序**

![](.gitbook/assets/screen-shot-2019-07-14-at-5.27.38-pm.png)

initial loading:

constructor called. 

render\(\) called.

 componentDidMount\(\) called. \(only once\)

component changes:

shouldComponentUpdate\(\) called.\(if there is any\)

then 

componentDidUpdate\(\) called.\(every time when state/props changes\)

## **8.Why react has good performance**

**React’s** use of a **virtual DOM** is one of its features that makes it so blazingly fast.  A **virtual DOM** only looks at the differences between the previous and current HTML and changes the part that is required to be updated. 



Conversely, Angular opted to use a **regular DOM.** This will update the entire tree structure of HTML tags until it reaches the user’s age.  


#### **React Fiber: \(after version 16\)**

With Fiber, react can pause and resume work as it sees fit to get what matters onto the screen as quickly as possible. I

\*\*\*\*

## **9. Difference between framework and libraries**

**library vs framework:**

A software framework \(be it front-end or backend\) includes standardized, pre-written code, which makes the development of certain functionalities easier and faster. You have less freedom to code, as you have to code as the framework architecture dictates.

A library is a collection of functions and functionalities, which you can use to achieve a certain end. You have more freedom to design and construct the system when using a library, but that adds more responsibility on the coder to be able to use it efficiently and find the right library for the right job, because, for projects which need to grow over time and become more serious, this could become significantly riskier and more difficult to manage.

The most significant difference between a framework and a library is how they interact with your code.

Your code calls the library while the framework calls your code.

This is also known as Inversion of Control. The litmus test for detecting a framework is checking if it has the Inversion of Control.

## **10.props and state**

Props is shorthand for properties, and Props are how components talk to each other by passing values around.

**class components:**

```text
import React, {Component} from 'react';

class Text extends Component {
  render() {
    console.log(this.props);
    // {
    //   text: "Hello World."
    // }
    return <p>{this.props.text}</p>;
  }
}

class App extends Component {
  render() {
    return <Text text="Hello World." />;
  }
}
```

**function component:**

```text
import React, {Component} from 'react';

function Text(props) {
  console.log(props);
  // {
  //   text: "Hello World."
  // }
  return <p>{props.text}</p>;
}
function App(props) {
  return <Text text="Hello World." />;
}
```

## **11.end-to-end test tool and unit test tool**

## **12.**PropTypes**?**



As your app grows, you can catch a lot of bugs with typechecking. For some applications, you can use JavaScript extensions like Flow or TypeScript to typecheck your whole application. But even if you don’t use those, React has some built-in typechecking abilities. To run typechecking on the props for a component, you can assign the special propTypes property:

Before we use `React.PropTypes` to do the typechecking. Since React v15.5, it has been moved into a different package called `prop-types`.

To insatll `prop-types`:

```text
npm install prop-types --save
```

Example:

```text
import React, {Component} from 'react';
import PropTypes from 'prop-types';

class TextA extends Component {
  render() {
    return <p>Hello, {this.props.text}</p>;
  }
}

const TextB = props => {
  return <p>Hello, {props.text}</p>;
};

TextA.propTypes = {
  text: PropTypes.string,
};

TextB.propTypes = {
  text: PropTypes.string,
};
```

Here is a list of all available types:

```text
MyComponent.propTypes = {
  // You can declare that a prop is a specific JS type. By default, these
  // are all optional.
  optionalArray: PropTypes.array,
  optionalBool: PropTypes.bool,
  optionalFunc: PropTypes.func,
  optionalNumber: PropTypes.number,
  optionalObject: PropTypes.object,
  optionalString: PropTypes.string,
  optionalSymbol: PropTypes.symbol,

  // Anything that can be rendered: numbers, strings, elements or an array
  // (or fragment) containing these types.
  optionalNode: PropTypes.node,

  // A React element.
  optionalElement: PropTypes.element,

  // You can also declare that a prop is an instance of a class. This uses
  // JS's instanceof operator.
  optionalMessage: PropTypes.instanceOf(Message),

  // You can ensure that your prop is limited to specific values by treating
  // it as an enum.
  optionalEnum: PropTypes.oneOf(['News', 'Photos']),

  // An object that could be one of many types
  optionalUnion: PropTypes.oneOfType([
    PropTypes.string,
    PropTypes.number,
    PropTypes.instanceOf(Message)
  ]),

  // An array of a certain type
  optionalArrayOf: PropTypes.arrayOf(PropTypes.number),

  // An object with property values of a certain type
  optionalObjectOf: PropTypes.objectOf(PropTypes.number),

  // An object taking on a particular shape
  optionalObjectWithShape: PropTypes.shape({
    color: PropTypes.string,
    fontSize: PropTypes.number
  }),

  // You can chain any of the above with `isRequired` to make sure a warning
  // is shown if the prop isn't provided.
  requiredFunc: PropTypes.func.isRequired,

  // A value of any data type
  requiredAny: PropTypes.any.isRequired,

```

##  **13.Can react work with angular.js? What’s the problem of doing that?**

##  **15.What is component and Props?**

React components are like JavaScript functions. They accept arbitrary inputs \(called “props”\) and return React elements describing what should appear on the screen.

Building a React project involves creating one or more React components that can interact with each other. A React component is simply a JavaScript class that requires the render function to be declared. The render function simply outputs HTML code, which is implemented using either JSX. A React component may also require additional functions for handling data, actions and lifecycle events.

React components can further be categorized into containers/stateful components and stateless components. A stateless component’s work is simply to display data that it receives from its parent React component. It can also receive events and inputs, which it passes up to its parent to handle. A React container or stateful component does the work of rendering one or more child components. It fetches data from external sources and feeds it to its child components. It also receives inputs and events from them in order to initiate actions.

Components let you split the UI into independent, reusable pieces, and think about each piece in isolation.

**Props:**

Props is shorthand for properties, and Props are how components talk to each other by passing values around.

## **16.**ReactDOM.render\(, document.getElementById\('root'\)\) ?

* We call ReactDOM.render\(\) with the `<App />` component, to render `<App />` inside `<div id="root"></div>`.
* Our App component returns a `<div>Hello World!!!</div>` as the result.
* React DOM efficiently updates the HTML DOM to match `<div>Hello World!!!</div>`.

##  **17.How to handle event in react\(2 kinds?\)?**

a.

```text
class Toggle extends React.Component {
  constructor(props) {
    super(props);
    this.state = {isToggleOn: true};

    // This binding is necessary to make `this` work in the callback
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState(prevState => ({
      isToggleOn: !prevState.isToggleOn
    }));
  }

  render() {
    return (
      <button onClick={this.handleClick}>
        {this.state.isToggleOn ? 'ON' : 'OFF'}
      </button>
    );
  }
}

ReactDOM.render(
  <Toggle />,
  document.getElementById('root')
);
```

b. arrow function

```text
class Toggle extends React.Component {
  constructor(props) {
    super(props);
    this.state = {isToggleOn: true};

    // This binding is necessary to make `this` work in the callback
    // this.handleClick = this.handleClick.bind(this);
  }

  handleClick = () => {
    this.setState(prevState => ({
      isToggleOn: !prevState.isToggleOn
    }));
  }

  render() {
    return (
      <button onClick={this.handleClick}>
        {this.state.isToggleOn ? 'ON' : 'OFF'}
      </button>
    );
  }
}

ReactDOM.render(
  <Toggle />,
  document.getElementById('root')
);
```

## **18.what life cycle to do async calls**

componentDidMount\(\)**;**

##  19.**what is ref, give a scenario using ref**

Refs provide a way to access DOM nodes or React elements created in the render method.

In the typical React dataflow, [props](https://reactjs.org/docs/components-and-props.html) are the only way that parent components interact with their children. To modify a child, you re-render it with new props. However, there are a few cases where you need to imperatively modify a child outside of the typical dataflow. **The child to be modified could be an instance of a React component, or it could be a DOM element.** For both of these cases, React provides an escape hatch.

####  <a id="when-to-use-refs"></a>

#### When to use Refs <a id="when-to-use-refs"></a>

There are a few good use cases for refs:

* Managing focus, text selection, or media playback.
* Triggering imperative animations.
* Integrating with third-party DOM libraries.

**Avoid using refs for anything that can be done declaratively.**

\*\*\*\*

* When the `ref` attribute is used on an HTML element, the `ref` created in the constructor with `React.createRef()` receives the underlying DOM element as its `current` property.
* When the `ref` attribute is used on a custom class component, the `ref` object receives the mounted instance of the component as its `current`.

**???**

\*\*\*\*



## **20.how to communicate between parent and child component?**

```text
import ReactDOM from "react-dom";

import React, { Component } from 'react';

class Parent extends React.Component {
  constructor(props) {
    super(props);

    this.state = {
      fieldVal: ""
    }
  }

  onUpdate = (val) => {
    this.setState({
      fieldVal: val
    })
  };

  render() {
    return (
      <div>
        <h2>Parent</h2>
        Value in Parent Component State: {this.state.fieldVal}
        <br/>
        <Child onUpdate={this.onUpdate} />
        <br />
        <OtherChild passedVal={this.state.fieldVal} />
      </div>
    )
  }
}

class Child extends React.Component {
  constructor(props) {
    super(props);

    this.state = {
      fieldVal: ""
    }
  }

  update = (e) => {
    console.log(e.target.value);
    this.props.onUpdate(e.target.value);
    this.setState({fieldVal: e.target.value});
  };

  render() {
    return (
      <div>
        <h4>Child</h4>
        <input
          type="text"
          placeholder="type here"
          onChange={this.update}
          value={this.state.fieldVal}
        />
      </div>
    )
  }
}

class OtherChild extends React.Component {
  render() {
    return (
      <div>
        <h4>OtherChild</h4>
        Value in OtherChild Props: {this.props.passedVal}
      </div>
    )
  }
}

const rootElement = document.getElementById("root");
ReactDOM.render(<Parent />, rootElement);

```

## 22.**forceUpdate? when to use that?**

By default, when your component’s state or props change, your component will re-render. If your `render()` method depends on some other data, you can tell React that the component needs re-rendering by calling `forceUpdate()`.

Calling `forceUpdate()` will cause `render()` to be called on the component, skipping `shouldComponentUpdate()`. This will trigger the normal lifecycle methods for child components, including the `shouldComponentUpdate()` method of each child. React will still only update the DOM if the markup changes

\*\*\*\*

## **23.when to choose library/framework & why?**

**library\(react\) is good for:**

* **Dynamic Applications:** React will be a great choice because it uses a virtual DOM. It can quickly incorporate and "react" to the data changes made in the view by the users.
* **Single Page Apps:** React will be a great solution because it can display all changes made to the content without reloading the current page.
* **Native Mobile Apps:** If you wish to create a native mobile app, there is nothing better than React Native. You will be creating apps written in JavaScript with equal performance and feel of apps created in Java or Objective-C. **Angular** is ideal if you have a large application and you need strict code structure and base.

framework is good for:



* **Cross-platform Mobile Apps:** Angular 2 has great support for mobile apps, as it was created for that very purpose. It addresses limiting factors such as navigation via touch, different screen sizes, and mobile hardware.
* **Enterprise Software:** Because Angular uses an MVC architecture, it is great for creating enterprise level apps.
* **Progressive Web Apps and Hybrid Mobile Apps:** Angular 2, in combination with Ionic 2, is a perfect tool for building hybrid apps. The same technology stack can be used for progressive web app development. Angular 2 \(and up\) comes with a mobile toolkit which makes developing mobile apps extremely easy and quick.





##  24.**react play as view, what is mvc structure?**

![](.gitbook/assets/image.png)

\*\*\*\*

* **Model** − The lowest level of the pattern which is responsible for maintaining data.
* **View** − This is responsible for displaying all or a portion of the data to the user.
* **Controller** − Software Code that controls the interactions between the Model and View.

MVC is popular as it isolates the application logic from the user interface layer and supports separation of concerns. Here the Controller receives all requests for the application and then works with the Model to prepare any data needed by the View. The View then uses the data prepared by the Controller to generate a final presentable response. The MVC abstraction can be graphically represented as follows.

##  **27.react 缺点**

High pace of development

 Poor documentation

 ‘HTML in my JavaScript!’ **–** JSX as a barrier

 Additional SEO hassle

## **28.angular优缺点**

Pros of AngularJS**:**

  **Two-way data binding**:Two-way data binding allowed engineers to reduce development time as it didn’t require writing additional code to provide continual View and Model synchronization

  **Directives.** This feature actually enabled the HTML extension mentioned above. 

   **Dependency injection.** Dependencies define how different pieces of code interact with each other and how the changes in one component impact the other ones. 

  **Community**

Cons of AngularJS**:**

  **Performance.** Dynamic applications didn’t always perform that well. Complex SPAs could be laggy and inconvenient to use due to their size.

  **Steep learning curve.** As AngularJS is a versatile instrument, there is always more than one way to complete any task. This has produced some confusion among engineers.

## **29.What part of the MVC pattern does ReactJS implement?** 

**V**

## 30.**What frameworks have you used in conjunction with ReactJS for routing, AJAX calls, and other Model and Controller functionality that is not provided by ReactJS?**

## **31. Explain what a Component is and how it is created.**

React components are like JavaScript functions. They accept arbitrary inputs \(called “props”\) and return React elements describing what should appear on the screen.

Building a React project involves creating one or more React components that can interact with each other. A React component is simply a JavaScript class that requires the render function to be declared. The render function simply outputs HTML code, which is implemented using either JSX. A React component may also require additional functions for handling data, actions and lifecycle events.

React components can further be categorized into containers/stateful components and stateless components. A stateless component’s work is simply to display data that it receives from its parent React component. It can also receive events and inputs, which it passes up to its parent to handle. A React container or stateful component does the work of rendering one or more child components. It fetches data from external sources and feeds it to its child components. It also receives inputs and events from them in order to initiate actions.

Components let you split the UI into independent, reusable pieces, and think about each piece in isolation.

**function component:**

```text
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

 **class component:**

```text
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

**Pass data between function components:**

```text
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App() {
  return (
    <div>
      <Welcome name="Sara" />
      <Welcome name="Cahal" />
      <Welcome name="Edite" />
    </div>
  );
}

ReactDOM.render(
  <App />,
  document.getElementById('root')
);
```

## **32.which function  would you write when you wanna get data from server?**

```text
export const getUsers = () => dispatch => {
  // console.log(userData);
  axios
    .get("/api/users/all")
    .then(res =>
      dispatch({
        type: GET_USERS,
        payload: res.data
      })
    )
    .catch(err =>
      dispatch({
        type: GET_USERS,
        payload: null
      })
    );
};
```

## **33.what is the data binding advantage for ReactJS and AngularJs**

\*\*\*\*

\*\*\*\*

## **34.http request with different method\(put, get, delete,\) and status**

GET The GET method requests a representation of the specified resource. Requests using GET should only retrieve data.

 HEAD The HEAD method asks for a response identical to that of a GET request, but without the response body.

 POST The POST method is used to submit an entity to the specified resource, often causing a change in state or side effects on the server. 

PUT The PUT method replaces all current representations of the target resource with the request payload.

DELETE The DELETE method deletes the specified resource

. CONNECT The CONNECT method establishes a tunnel to the server identified by the target resource.

OPTIONS The OPTIONS method is used to describe the communication options for the target resource. 

TRACE The TRACE method performs a message loop-back test along the path to the target resource.

PATCH The PATCH method is used to apply partial modifications to a resource.

返回的状态码和状态不一致的情况是有可能发生得 比如Web应用程序内部错误，但仍然返回 200 OK

200 OK 请求正常处理完毕 

204 No Content 请求成功处理，没有实体的主体返回 206 Partial Content GET范围请求已成功处理 

301 Moved Permanently 永久重定向，资源已永久分配新URI 302 Found 临时重定向，资源已临时分配新URI

 303 See Other 临时重定向，期望使用GET定向获取 304 Not Modified 发送的附带条件请求未满足 3

07 Temporary Redirect 临时重定向，POST不会变成GET 400 Bad Request 请求报文语法错误或参数错误 

401 Unauthorized 需要通过HTTP认证，或认证失败 

403 Forbidden 请求资源被拒绝 

404 Not Found 无法找到请求资源（服务器无理由拒绝） 

500 Internal Server Error 服务器故障或Web应用故障 

503 Service Unavailable

服务器超负载或停机维护

## **300?400?500?200?都什么意思 其中server反应时间怎么看呢？多长时间返回数据从后端** 

## 35.**React, Redux 的关系图是什么样子的，白板给我画一下**

![](.gitbook/assets/image%20%281%29.png)

## **36.react+redux怎么传data，props怎么往上传，怎么跨页面传东西 如果不用redux怎么传    如果还不能用react怎么传     react router用法**

## **37.如果不用react，怎么储存传进来的一大堆数据 //dom，localStorege**

## **38.what is react.lazy\(\),** mapstatetoprops ,mapdispatchtoprops

The `React.lazy` function lets you render a dynamic import as a regular component.  


```text
const OtherComponent = React.lazy(() => import('./OtherComponent'));

function MyComponent() {
  return (
    <div>
      <OtherComponent />
    </div>
  );
}
```

mapstatetoprops_:_

`mapStateToProps` is used for selecting the part of the data from the store that the connected component needs. It’s frequently referred to as just `mapState` for short.

* It is called every time the store state changes.
* It receives the entire store state, and should return an object of data this component needs.

```text
function mapStateToProps(state) {
  const { todos } = state
  return { todoList: todos.allIds }
}

export default connect(mapStateToProps)(TodoList)
```

mapdispatchtoprops_:_

`mapDispatchToProps` is used for dispatching actions to the store.

`dispatch` is a function of the Redux store. You call `store.dispatch` to dispatch an action. This is the only way to trigger a state change.

[  
](https://react-redux.js.org/using-react-redux/connect-mapstate#defining-mapstatetoprops)

```text
const mapDispatchToProps = dispatch => {
  return {
    // dispatching plain actions
    increment: () => dispatch({ type: 'INCREMENT' }),
    decrement: () => dispatch({ type: 'DECREMENT' }),
    reset: () => dispatch({ type: 'RESET' })
  }
}
```

## _41. if I have a large json data response, what would you do to store in front end_

\*\*\*\*

_a._paginate your response data from serverside first to reduce the size of the json object.

b. parallel render then ui by chunk

c. don't do deep watch in the data if the data is too big, for example don't ngRepeat for too many data, if two way binding is not nessary. that will make your application very slow

## 42.**what is the react works in FLUX?**

\*\*\*\*

| Redux | Flex |
| :--- | :--- |
| one store | multiple store |
| multiple reducers | no reducer |
| implemented dispatch function | have to implement dispatch |
| library | pattern |
| implemented based on flux |  |

## 



## **44.what is JSX**

JSX is a syntax extension to JavaScript. It is similar to a template language, but it has full power of JavaScript. JSX gets compiled to `React.createElement()` calls which return plain JavaScript objects called “React elements”.

```text
// JSX
return (
    <div className="App"> 
        <h1>React</h1>
    </div>
);

// JavaScript
return React.createElement("div", {className: "App"}, 
    React.createElement("h1", null, "React"));
```

_Why JSX React_ **:**

embraces the fact that rendering logic is inherently coupled with other UI logic: how events are handled, how the state changes over time, and how the data is prepared for display. Instead of artificially separating technologies by putting markup and logic in separate files, React separates concerns with loosely coupled units called "components" that contain both.

## **45.element vs component**

Element vs Component

| Element | Component |
| :--- | :--- |
| the tag of an object representation of a DOM node | a function or a class which optionally accepts input and returns a React element |

## **46.React.createElement\(\)**

Create and return a new [React element](https://reactjs.org/docs/rendering-elements.html) of the given type. The type argument can be either a tag name string \(such as `'div'` or `'span'`\), a [React component](https://reactjs.org/docs/components-and-props.html) type \(a class or a function\), or a [React fragment](https://reactjs.org/docs/react-api.html#reactfragment) type.

Code written with [JSX](https://reactjs.org/docs/introducing-jsx.html) will be converted to use `React.createElement()`. You will not typically invoke `React.createElement()` directly if you are using JSX. See [React Without JSX](https://reactjs.org/docs/react-without-jsx.html) to learn more.

```text
React.createElement(
  type,
  [props],
  [...children]
)
```

\*\*\*\*

\*\*\*\*

## **48.state vs props**

**State** is referred to the local state of the component which cannot be accessed and modified outside of the component and only can be used & modified inside the component. **Props,** on the other hand, ****make components reusable by giving components the ability to receive data from the parent component in the form of props.  


\*\*\*\*

## **49.how to maintain state for your project**

## **50.second parameter in setState\(\)**

```text
setState(updater[, callback])

```

\*\*\*\*

## **51.how to output array in react**

```text
function ListItem(props) {
  // Correct! There is no need to specify the key here:
  return <li>{props.value}</li>;
}

function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map((number) =>
    // Correct! Key should be specified inside the array.
    <ListItem key={number.toString()}
              value={number} />

  );
  return (
    <ul>
      {listItems}
    </ul>
  );
}

const numbers = [1, 2, 3, 4, 5];
ReactDOM.render(
  <NumberList numbers={numbers} />,
  document.getElementById('root')
);
```

## **52.what test method you use for React**

Jest and Enzyme



## **53.how to prevent a component from rendering**

* return null in the render method function
* return false in shouldComponentUpdate\(\) lifecycle method function in class based component

## **54.how to do auth in React**

Auth0

## **56. react state vs redux state, when do you use redux**

React state is stored locally within a component. When it needs to be shared with other components, it is passed down through props. 

When using Redux, state is stored globally in the Redux store. Any component that needs access to a value may subscribe to the store and gain access to that value. 

when to use redux:

**a.** Same piece of application state needs to be mapped to multiple container components.

b. Global components that can be accessed from anywhere.

c.Too many props are being passed through multiple hierarchies of components.

d.State management using setState is bloating the component.

f.Caching page state



## **57.write a router to route different component.**

\*\*\*\*

\*\*\*\*



##  

59.

**shouldComponentupdate.**

**when to use it.** 

**how to use it.**

**is this function check this state or next state.**

**how to check state changes.**  


## 60. **how to access dom tree node, when to use Refs**

**61.前端怎么通过URL拿取json数据**

**62. controlled components/ uncontrolled components.**

\*\*\*\*

\*\*\*\*

**64.Prevent default**

\*\*\*\*

**69. Forward refs**

**70. Error boundaries**

**71.class component vs function component，使用环境**

**72.怎么提升react效率**

**73.为什么要用redux，为什么不用context api**

**74.eject 用过吗**

**npm run eject上面提到，脚手架为了"优雅",隐藏了所有的webpack相关配置文件，如果我们想要基于原来的基础再次增加一些自己的东西，首先就要找到这些隐藏文件并且进行修改。**

**有的开发者直接到node\_modules中去搜索webpack.config...等文件，然后进行修改，修改后发现生效了，但是当修改后，我们又安装了一些其它项目模块，重新编译的时候，又回到了原有的配置信息\(很头疼的问题，总不能每一次安装新模块后，都重新改一次需要修改的配置吧...\)**

**基于create-react-app创建完成项目后，会提供一个eject命令\($ yarn eject\)，基于这个命令，可以把隐藏的webpack文件展示出来，方便我们二次进行配置。**

**$yarn eject或者npm run eject 此命令执行完成不可逆转\(慎重使用\)**

**执行完成后，我们可以看到原有的结构目录发生了一些变化\(新增两个文件夹,package.json中的内容也跟着发生改变\)**  


75.**用哪个版本的react，新版本的新特性有哪些**

**76.Why virtual DOM is faster than real DOM?**

77.**sometime, response json file has empty field. how to do?**  

**hard to handle from front end**  


78.

**问我, 听说你之前用过reusable Component, 能具体说说都是怎么用的吗? 我说用过的reusable Component里面,  button类型的用过的最多, 看她貌似不太满意, 我就又说form我也用过reusable Component, 并解释说reusable Component就类似一个Component的基本框架, 想要用的时候就添加新的feature或者function就行了, 如果想要使用的话, 任何8一个Component都可以是reusable Component, 看她貌似满意, 我就没再继续BB了**

**79.然后问我Component, reducer和actionCreator之前怎么联系在一块的**

**80.**

**解释React Hooks,解释React Context API,解释React Context API 和 Redux的区别，更喜欢哪个**

**81.**

**how many ways to create a react component?**

**follow up: what is the difference between functional component and class component.**

**which one has better performance do you think?**

**what is react hook? give an example （让我在白板上写react hook example代码, 因为上个问题回答答到了hook）**

**82.**

**写个React Component去request一个list, 按她想要的做个mapping，很基本的东西。**

**state改变了，如何阻止render, shouldComponentUpdate\(\) { return false}**  


**83.what is synthetic event?**

**84.如何clean up event handler**

**85.什么引起了react update?**

**86.flux vs react**

**87.if you cannot render correctly, what will you do?**

**I talked about redux state check and the value of the states, Unit test ,and system test.**  


88.**props  vs state can we directly change state**

**89.why we use root in React**

**90.do you know react fibre**

91.**react fragment**

**92.tree shaking of react**

**93.do you know something new about react like react pwa?**

**94. authorization besides JWT**

**95.what is the difference between react and mvc**

**96.how to prevent re-render**

**97.react native vs react**

**98. what is container layer  in the redux? Container layer?**

**99. flux flow vs redux**

**100.What is the purpose of render function?**

101.**What method will trigger in re-render page**

**Component should update**  


102.**what is curry**

**103.Event driven model**

**104.Difference between reactjs and jquery**

**105. Pure function,**   


106.**how to persist your data\(大概意思是说如何不让信息暴露给所有人**

**107.What will happen if you do this.setState in render function**

**108.proptypes this is used validate the props that is fetched from the parent**

          **proptypes is a package**

  
109.**React router**

**110. arguments of createStore\(\) ? \(reducer, \[preloadedState\], \[enhancer\]\)**

**111.同时有2个Async calls，你怎么handle？一个接一个，or同时？**

**112.How a button works from user Click to updates rendering on the page?**

**113.Write an easy helloWorld Component \(using codesandbox\)**

  
  


\*\*\*\*

  
  


  


  


\*\*\*\*

  


\*\*\*\*

\*\*\*\*

  




