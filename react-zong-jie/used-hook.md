# Used Hook

## useState

useState\(\) returns an array with exactly two elements: 

\(1\) Your current state value, \(2\) A method to update your state value.

useState\(\) will replace the old state instead of merging. 

```jsx
import React, { useState } from "react";
import Person from "./Person/Person";

const App = props => {
    const [personState, setPersonState] = useState({
        person: [
            { name: "Harry", age: 24 }
        ]
    });
    
    const [otherState, setOtherState] = useState("some other value");
    
    const switchNameHandler = () => {
        setPersonState({
            person: [
                {name: "Harry Lu", age: 25}
            ]
        });
    };
    
    return (
        <div className="App">
            <button onClick={switchNameHandler}>Switch Name</button>
            <Person
                name={personState.person[0].name}
                age={personState.person[0].age}
            /> 
        </div>
    );
}

export default App;
```

## useEffect & useRef & useContext

```jsx
import React, { useEffect, useRef, useContext } from 'react';
import AuthContext from '../../context/auth-context';

const cockpit = props => {
  const toggleBtnRef = useRef(null);
  const authContext = useContext(AuthContext);

  useEffect(() => {
    // Http request...
    // same as componentDidMount and componentDidUpdate
    // setTimeout(() => {
    //   alert('Saved data to cloud!');
    // }, 1000);
    toggleBtnRef.current.click();
    return () => {
      // clean-up code here
      // same as componentWillUnmount 
    };
  }, []); // only re-run the effect if the value inside changes

  return (
    <div>
      <button ref={toggleBtnRef}>
        Toggle Persons
      </button>
      <button onClick={authContext.login}>Log in</button>
    </div>
  );
};

export default React.memo(cockpit);
```

## Counter Example

```jsx
import React, { useState } from "react";

const App = (props) => {

  const [counter, setCounter] = useState(0);

  return (
    <React.Fragment>
      <span>You Clicked {counter} times!</span>
      <button onClick={() => setCounter(counter + 1)}>Increase</button>
      <button onClick={() => setCounter(counter - 1)}>Decrease</button>
    </React.Fragment>
  );
}

export default App;
```

## React Counter using Hooks

```jsx
import React, { useState, useEffect } from "react";
import ReactDOM from "react-dom";

function App() {
  const [num, setNum] = useState(Number(localStorage.getItem("num")) || 0);

  useEffect(() => {
    localStorage.setItem("num", num);
  }, [num]);

  return (
    <div>
      {num}
      <button onClick={() => setNum(num + 1)}>Add</button>
      <button onClick={() => setNum(num - 1)}>Subtract</button>
    </div>
  );
}

ReactDOM.render(<App />, document.getElementById("root"));
```

