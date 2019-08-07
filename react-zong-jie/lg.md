# LG

```jsx
import React, { Component } from 'react';

class Clock extends Component {
  constructor(props) {
    super(props);
    this.state = {
      time: null
    }
  }

  componentDidMount() {
    this.timeId = setInterval(this.tick, this.props.interval || 1000);
  }

  tick = () => {
    let currTime = new Date();
    let h = currTime.getHours();
    let m = currTime.getMinutes();
    let s = currTime.getSeconds();
    this.setState({
      time: h + ':' + m + ':' + s
    });
  }

    render() {
      return (
        <div>
          {this.state.time}
        </div>
      );
    }

    componentWillUnmount() {
      clearInterval(this.timeId);
    }
  }

  export default Clock;

```

```jsx
import React from "react";
import ReactDOM from "react-dom";
import Clock from "./Clock";

import "./styles.css";

function App() {
  return (
    <Clock />
  );
}

const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);

```

## **super\(\):** 

 super\(\) will calls the constructor of its parent class. This is required when you need to access some variables from the parent class.In React, when you call super with props. React will make props available across the component through this.props. 

## **why use arrow function**:

One obvious benefit of arrow functions is to simplify the syntax needed to create functions, without a need for the function keyword. The this within arrow functions is also bound to the enclosing scope which is different compared to regular functions where the this is determined by the object calling it.

## second argument of setState:

setState\(updater\[, callback\]\)

## Pros for single quotes: 

One popular argument for single quotes is when you have to write html within javascript: If you use single quotes you can write var html = '' If you use double quotes you must escape each nested " EX: var html = "" which can get annoying. Or you could use single quotes within the html string, but I don't want to cover quotes for html here \(that would just hurt\)... Single quotes can often look better when you're using them to represent an empty string '' vs "" \(too many little marks in the latter and can be difficult read - ahhh\)

Only real con I can come up with is copying/pasting between JSON and JavaScript files - single quotes are not supported within JSON files, so you'd have to do a host of search/replace \(and escaping of double quotes\)...

## Life Cycle

**componentWillUnmonut\(\)**: componentWillUnmount\(\) is invoked immediately before a component is unmounted and destroyed.

**componentDidMount\(\)**: componentDidMount\(\) is invoked immediately after a component is mounted.

