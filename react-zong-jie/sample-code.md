# Sample Code

## Class Component - Containers, Smart, Stateful

no state, no life cycle, commonly referred to as stateless components.

```jsx
import React, { Component } from "react";
import Person from "./Person/Person";

class App extends Component {
    state = {
        person: [
            {name: "Harry", age: 24}
        ]
    };
    
    switchNameHandler = (newName) => {
        this.setState({
            person: [
                {name: newName, age: 24}
            ]
        });
    };
    
    nameChangedHandler = (event) => {
        this.setState({
            person: [
                {name: event.target.value, age: 24}
            ]
        });
    };
    
    render() {
        return (
            <div className="App"> 
                // first way to pass arugments to event handlers
                <button onClick={() => this.switchNameHandler("Harry Lu")}>Switch Name</button>
                <Person 
                    name={this.state.person[0].name}
                    age={this.state.person[0].age}
                    // second way to pass augments to event handlers
                    click={this.switchNameHandler.bind(this, "Harry!!!")}
                    changed={this.nameChangedHandler}
                > My Hobbies: Sing, Dance, Rap, Basketball
                </Person>
            </div>
        );
    }
} 

export default App;
```

## Functional Component - Presentational, Dumb, Stateless

```jsx
import React from "react";

const person = (props) => {
    return (
        <div>
            <p> onClick={props.click} I'm {props.name} and I am {props.age} years old!</p>
            <p>{props.children}</p> // anything between the parent's opening and closing tag
            <input type="text" onChange={props.changed} value={props.name} /> // two way data binding 
        </div>
    );
};

export default person;
```

## Three way to handle events 

* Bind this in the constructor

```jsx
constructor(props) {
    super(props);
    this.state = {};
    this.handleClick = this.handleClick.bind(this);
}
```

* Using arrow functions

```jsx
handleClick = () => {
    console.log("this is:", this);
}
```

* Using arrow functions in the callback - Since callback is created each time the button renders. If this callback is passed as a prop to lower components, those components might do an extra re-rendering, which will cause performance problems. 

```jsx
render() {
    return (
        <button onClick={(e) => this.handleClick(e)}> Click me </button>
    );
}
```

## ErrorBoundary 

```jsx
// must wrap the code you want to test using high order components 
import React, { Component } from 'react';

class ErrorBoundary extends Component {
  state = {
    hasError: false,
    errorMessage: ''
  }
  
  static getDerivedStateFromError(error) {
    // update state so the next render will show the fallback UI.
    return { hasError: true };
  }

  componentDidCatch = (error, info) => {
    // you can also log the error to an error reporting service
    // logErrorToMyService(error, info);
    this.setState({ hasError: true, errorMessage: error });
  }

  render() {
    if (this.state.hasError) {
      // you can render any custom fallback UI
      return <h1>{this.state.errorMessage}</h1>;
    } 
    return this.props.children;
  }
}

export default ErrorBoundary;
```

## Three ways using Higher Order Component

```jsx
// This one just do wrap other component
const aux = props => props.children; 

export default aux;
```

```jsx
// This one just add styling to the children component
import React from 'react';

// const withClass = props => (
//   <div className={props.classes}>
//     {props.children}
//   </div>
// );

const withClass = (WrappedComponent, className) => {
  return props => (
    <div className={className}>
        // getting the props from the child compoent
        <WrappedComponent {...props}/> 
    </div>
  );
}

export default withClass;
```

```jsx
// This is the built-in way that works same as the first one
import React, {Fragment} from 'react';

<Fragment>
    // some content
</Fragment>
```

## 

## Better way to use setState\(\)

```jsx
// the better way to update the state when you are depending on old state
// Since setState updates the state asynchronously
this.setState((state, props) => {
    return {
        counter: state.counter + props.increment
    };
});
```

## Render Lists Conditionally

```jsx
import React, { Component } from 'react';
import Person from './Person/Person';

class App extends Component {
  state = {
    persons: [
      { id: 'a1', name: 'Harry', age: 24 },
      { id: 'a2', name: 'Sherry', age: 21 },
      { id: 'a3', name: 'Steven', age: 26 }
    ],
    otherState: 'some other value',
    showPersons: false
  }

  nameChangedHandler = (event, id) => {
    const personIndex = this.state.persons.findIndex(p => {
      return p.id === id;
    })

    const person = {
      ...this.state.persons[personIndex]
    };

    // const person = Object.assign({}, this.state.persons[personIndex]);

    person.name = event.target.value;

    const persons = [...this.state.persons];
    persons[personIndex] = person;

    this.setState({ persons: persons });
  }

  deletePersonHandler = (personIndex) => {
    // const persons = this.state.persons.slice();
    // Updating State Immutably
    const persons = [...this.state.persons];
    persons.splice(personIndex, 1);
    this.setState({ persons: persons });
  }

  togglePersonsHandler = () => {
    const doesShow = this.state.showPersons;
    this.setState({ showPersons : !doesShow});
  }

  render() {
    let persons = null;

    if (this.state.showPersons) {
      persons = (
        <div>
          {this.state.persons.map((person, index) => {
            return <Person 
              click={() => this.deletePersonHandler(index)}
              name={person.name} 
              age={person.age}
              key={person.id}
              changed={(event) => this.nameChangedHandler(event, person.id)} />
          })}
        </div>
      )
    }
    return (
      <div className="App">
        <h1>Hi, I'm a React App</h1>
        <p>This is really working!</p>
        <button 
          onClick={this.togglePersonsHandler}>Switch Name</button>
        {persons}
      </div>
    );
  }
}

export default App;
```

## Controlled Component

In HTML, form elements such as `<input>`, `<textarea>`, and `<select>` typically maintain their own state and update it based on user input. In React, mutable state is typically kept in the state property of components, and only updated with `setState()`.

We can combine the two by making the React state be the "single source of truth". Then the React component that renders a form also controls what happens in that form on subsequent user input. An input form element whose value is controlled by React in this way is called a "controlled component".

```jsx
class Form extends React.Component {
    state = { value: "" };
    handleChange = (event) => {
        this.setState({ value: event.target.value });
    };
    handleSubmit = (event) => {
        event.preventDefault();
        console.log(this.state.value);
    }
    render() {
        return (
            <form onSubmit={this.handleSubmit}>
                <label> Name:
                    <input type="text" value={this.state.value} onChange={this.handleChange} />
                </label>
                <input type="submit" value="Submit" />
            </form>
        );
    }
}
```

## Uncontrolled Component

```jsx
class Form extends React.Component {
    constructor(props) {
        super(props);
        this.handleSubmit = this.handleSubmit.bind(this);
        this.input = React.createRef();
    }
    
    handleSubmit(event) {
        event.preventDefault();
        console.log(this.input.current.value);
    }
    
    render() {
        return (
            <form onSubmit={this.handleSubmit}>
                <label> Name:
                    <input type="text" ref={this.input} />
                </label>
                <input type="submit" value="Submit" />
            <
        );
    }
}
```

## React Lazy & Suspense

`React.lazy` takes a function that must call a dynamic `import()`. This must return a `Promise` which resolves to a module with a default export containing a React component. 

```jsx
const MyComponent = React.lazy(() => import("./myComponent"));

function Component() {
    return (
        <div>
            <Suspense fallback={<div>Loading...</div>}>
                <MyComponent />
            </Suspense>
        </div>
    );
}
```

## Context & Ref & Fragment & PropTypes

```jsx
import React, { Component } from 'react';
import PropTypes from 'prop-types';
import classes from './Person.css';

class Person extends Component {
  constructor(props) {
    super(props);
    this.inputElementRef = React.createRef();
  }
  
  // creates a Context object. When React renders a component
  // that subscribes to this Context object it will read the 
  // current context value from the closest matching Provider
  // above it in the tree. 
  const AuthContext = React.createContext({
    authenticated: false,
    login: () => {}
  });

  static contextType = AuthContext;

  componentDidMount() {
    // this.inputElement.focus();
    this.inputElementRef.current.focus();
  }

  render() {
    return (
      <React.Fragment>
        // <AuthContext.Consumer>
        //  {context => 
        //    context.authenticated ? <p>Authenticated</p> : <p>Please log in</p>}
        // </AuthContext.Consumer>
        {this.context.authenticated ? (
          <p>Authenticated!</p>
        ) : (
          <p>Please log in</p>
        )}
        <p>{this.props.children}</p>
        <input
          // ref={(inputEl) => {this.inputElement = inputEl}}
          ref={this.inputElementRef}
          type="text"
          onChange={this.props.changed}
          value={this.props.name}
        />
      </React.Fragment>
    );
  }
}

Person.propTypes = {
  click: PropTypes.func,
  name: PropTypes.string,
  age: PropTypes.number,
  changed: PropTypes.func
};

export default Person;

// code in the parent file
<AuthContext.Provider
  value={{
    authenticated: this.state.authenticated,
    login: this.loginHandler
  }}
>
  <Person/>
</AuthContext.Provider>
```

## forwardRef

```jsx
// You can now get a ref directly to the DOM button
const ref = React.createRef();
<FancyButton ref={ref}>Click me!</FancyButton>;

const FancyButton = React.forwardRef((props, ref) => (
    // ref.current now point to the <button> DOM node
    <button ref={ref} {...props}> 
        {props.children}
    </button>
));
```

## Portals 

```jsx
render() {
    // React does not create a new div. It renders the children into domNode. 
    // domNode is any valid DOM node, regardless of its location in the DOM.
    return ReactDOM.createPortal(
        this.props.children,=
        domNode
    );
}
```

