# Redux 总结

## **redux**

Redux is an open-source JavaScript library for managing application state. The basic idea of redux is that the entire application state is kept in a single store. The store is simply a JavaScript object. The only way to change the state is by firing actions from your application and then writing reducers for these actions that modify the state. The entire state transition is kept inside reducers and should not have any side-effects. 

## redux architecture

![](.gitbook/assets/image%20%287%29.png)



## Why Redux is immutable

State is read-only. The only way to change the state is to emit an action, an object describing what happened. Inside a Redux application there is one particular function that takes the previous state and the action being dispatched, and returns the next state of the whole application. Reducer is the function knowing how to return a new state based on the action it receives. 

## Why state is immutable in Redux

Redux's use of shallow equality checking requires immutability if any connected components are to be update correctly. Immutability can bring increased performance to your app, and leads to simpler programming and debugging, as data that never changes is easier to reason about than data that is free to be changed arbitrarily throughout your app. In particular, immutability in the context of a Web app enables sophisticated change detection techniques to be implemented simply and cheaply, ensuring the computationally expensive progress of updating the DOM occurs only when it absolutely has to. 

#### Avoiding Array Mutations <a id="avoiding-array-mutations"></a>

#### Avoiding Object Mutations <a id="avoiding-object-mutations"></a>

## Redux vs Context API

Context API is built into React and you therefore need no extra third-party dependencies. e.g. You don't need a package like redux-thunk to handle asynchronous actions. 

The Context API is not built for high-frequency updates. It's only recommend for low-frequency updates \(e.g. theme changes, user authentication\) but not use it for the general state management of your application. 

## Shallow Equality Check vs Deep Equality Check

Shallow equality checking \(or reference equality\) simply checks that two different variables reference the same object; in contrast, deep equality checking \(or value equality\) must check every value of two object's properties.  

A shallow equality check is therefore as simple and as fast as `a === b`, whereas a deep equality check involves a recursive traversal through the properties of two objects, comparing the value of each property at each step.

It's for this improvement in performance that Redux uses shallow equality checking. 



## Action

Actions are plain JavaScript objects. They must have a type indicating the type of action being performed. In essence, actions are payload of information that send data from your application to your store. 

## Reducer

A reducer is simply a pure function that takes the previous state and an action, and returns the next state. 

```text
const counter = (state = 0, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1;
    case 'DECREMENT':
      return state - 1;
    default:
      return state;
  }
};

const increaseAction = {type: 'INCREMENT'};
const decreaseAction = {type: 'DECREMENT'};
const otherAction = {type: 'OTHER'};
```

## Store

The store is a JavaScript object that holds application state. Along with this it also has the following responsibilities:

* Allows access to state via getState\(\)
* Allows state to be updated via dispatch\(action\)
* Registers listeners via subscribe\(listener\)
* Handles unregistering of listeners via the function returned by subscribe\(listener\)

The only way to change the state inside it is to dispatch an action on it. 

```text
import {createStore} from 'redux';

const counter = (state = 0, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1;
    case 'DECREMENT':
      return state - 1;
    default:
      return state;
  }
};

const store = createStore(counter);
```

`store` has three important methods:

1. **`getState()`** retrieves the current state of the Redux store. If we ran `console.log(store.getState())` with the code above, we could get `0` since it is the initial state of our application.
2. **`dispatch()`** is the most commonly used. It is how we dispatch actions to change the state of the application. If we run `store.dispatch( { type: 'INCREMENT' });` followed by `console.log(store.getState());` we will get `1`.
3. **`subscribe()`** registers a callback that the redux store will call any time an action has been dispatched so you can update the UI of your application to reflect the current application state. If you have the function `print()` and you write `store.subscribe(print)`, the `print()` function will be called every time if an action has been dispatched.



## **why use redux**

Application state management that is easy to reason about, maintain and manage in an asynchronous web application environment. 

## **redux tool with different browser**

Redux DevTools

## **why use redux/ how to do async calls in redux**

```text
import fetch from 'cross-fetch'

export const REQUEST_POSTS = 'REQUEST_POSTS'
function requestPosts(subreddit) {
  return {
    type: REQUEST_POSTS,
    subreddit
  }
}

export const RECEIVE_POSTS = 'RECEIVE_POSTS'
function receivePosts(subreddit, json) {
  return {
    type: RECEIVE_POSTS,
    subreddit,
    posts: json.data.children.map(child => child.data),
    receivedAt: Date.now()
  }
}

export const INVALIDATE_SUBREDDIT = 'INVALIDATE_SUBREDDIT'
export function invalidateSubreddit(subreddit) {
  return {
    type: INVALIDATE_SUBREDDIT,
    subreddit
  }
}

// Meet our first thunk action creator!
// Though its insides are different, you would use it just like any other action creator:
// store.dispatch(fetchPosts('reactjs'))

export function fetchPosts(subreddit) {
  // Thunk middleware knows how to handle functions.
  // It passes the dispatch method as an argument to the function,
  // thus making it able to dispatch actions itself.

  return function(dispatch) {
    // First dispatch: the app state is updated to inform
    // that the API call is starting.

    dispatch(requestPosts(subreddit))

    // The function called by the thunk middleware can return a value,
    // that is passed on as the return value of the dispatch method.

    // In this case, we return a promise to wait for.
    // This is not required by thunk middleware, but it is convenient for us.

    return fetch(`https://www.reddit.com/r/${subreddit}.json`)
      .then(
        response => response.json(),
        // Do not use catch, because that will also catch
        // any errors in the dispatch and resulting render,
        // causing a loop of 'Unexpected batch number' errors.
        // https://github.com/facebook/react/issues/6895
        error => console.log('An error occurred.', error)
      )
      .then(json =>
        // We can dispatch many times!
        // Here, we update the app state with the results of the API call.

        dispatch(receivePosts(subreddit, json))
      )
  }
}
```

## **Redux流程**

**Redux question, like what is redux flow: view -&gt; action creator -&gt; action -&gt; middleware -&gt; reducer -&gt; store -&gt; view**

## **redux  thunk**

Redux thunk is a middleware that allows you to **write action creators that return a function instead of an action**. The thunk can then be used to delay the dispatch of an action if a certain condition is met. This allows you to handle the asynchronous dispatching of actions. This also allows you to dispatch multiple actions.

  


![](.gitbook/assets/image%20%285%29.png)

## **write redux thunk**

**//**enable Redux Thunk, use [`applyMiddleware()`](https://redux.js.org/api-reference/applymiddleware):

```text
import { createStore, applyMiddleware } from 'redux';
import thunk from 'redux-thunk';
import rootReducer from './reducers/index';

// Note: this API requires redux@>=3.1.0
const store = createStore(
  rootReducer,
  applyMiddleware(thunk)
);
```

```text
import store from "../store";

export const fetch_post = () => {
  return {
    type: "FETCH_USER"
  };
};

export const receive_post = post => {
  return {
    type: "FETCHED_USER",
    data: post
  };
};

export const receive_error = () => {
  return {
    type: "RECEIVE_ERROR"
  };
};

export const thunk_action_creator = username => {
  const user = username.replace(/\s/g, "");
  store.dispatch(fetch_post());
  return function(dispatch, getState) {
    return fetch(`https://api.github.com/users/${user}`)
      .then(data => data.json())
      .then(data => {
        if (data.message === "Not Found") {
          throw new Error("No such user found!!");
        } else dispatch(receive_post(data));
      })
      .catch(err => dispatch(receive_error()));
  };
};

```

## **difference between the Redux and Flux**

![](.gitbook/assets/image%20%286%29.png)

![](.gitbook/assets/image%20%288%29.png)



##  **Can you dispatch an action inside an action?**

**yes**

##  **Can you call an action inside reducer?**

**记得又问过我能不能在reducer里直接pass新的state数据给state, 我说不行, 因为reducer一定要是pure function, 不然不能work.** 

**问我reducer, actionCreator这些东西Component里面可以直接写和用, 为什么还要写在外面, 我也没听懂他想要问啥, 答了几句不得要领, 他就说那我直接问你吧, 为啥要用Redux, 我说React是single direction data flow, 要想传数据只能从parent往child传, 有了Redux之后想咋传就咋传\(我忘了说没用Redux的话, 用同一个parent并且把function通过props传给child, 这样来实现非parent-child的数据传递, 算是小遗憾\)**

## **写redux从”api/container” 里面得到{showContainer: true};**

##  **when to get api from redux;  redux why and where mapstatetoprops**  

\*\*\*\*

## **where to connect the redux**

```text
const mapStateToProps = state => ({
  errors: state.errors,
  users: state.users
});

export default connect(
  mapStateToProps,
  { editUser, getUsers }
)(withRouter(Edit));
```

## **when to unmount and why to unmount**

\*\*\*\*

## **three principles of redux, how to connect**

* Single source of truth - the state of your whole application is stored in an object tree within a single store.
* State is read-only - the only way to change the state is to emit an action, an object describing what happened.
* changes are made with **pure functions** - to specify how the state tree is transformed by actions, you write pure reducers. 

## **写一个redux的compoent，mapStateToProps, mapDispatchToProps** 

```text
import { connect } from 'react-redux'
import { toggleTodo } from '../actions'
import TodoList from '../components/TodoList'
import { VisibilityFilters } from '../actions'

const getVisibleTodos = (todos, filter) => {
  switch (filter) {
    case VisibilityFilters.SHOW_ALL:
      return todos
    case VisibilityFilters.SHOW_COMPLETED:
      return todos.filter(t => t.completed)
    case VisibilityFilters.SHOW_ACTIVE:
      return todos.filter(t => !t.completed)
    default:
      throw new Error('Unknown filter: ' + filter)
  }
}

const mapStateToProps = state => ({
  todos: getVisibleTodos(state.todos, state.visibilityFilter)
})

const mapDispatchToProps = dispatch => ({
  toggleTodo: id => dispatch(toggleTodo(id))
})

export default connect(
  mapStateToProps,
  mapDispatchToProps
)(TodoList)
```

\*\*\*\*

## **How to combine reducers**

```text
import { combineReducers } from "redux";
import errorReducer from "./errorReducer";
import userReducer from "./userReducer";
import managerReducer from "./managerReducer";

export default combineReducers({
  errors: errorReducer,
  users: userReducer,
  manager: managerReducer
});

```

## **redux middleware**

**thunk**

## When to use Redux

* Same piece of application state needs to be mapped to multiple container components. A good example of this is user state. When the app first loads, information about the user needs to be shared with various components in the navbar and each page. It’s likely these components don’t have any direct relationship so Redux provides a convenient way to share state.
* Too many props are being passed through multiple parent-and-child components.
* You want to separate state out of components for a better code structure

If the React project you’re working on doesn’t meet any of these criteria, then setState would likely do just fine. Redux really just becomes a tool to use in the right situation.

It is recommended to consider using Redux right from the start. Another opinion says to only start using Redux when you absolutely need it. However, in most of the cases, state management can get ugly and hard to maintain very quickly.

## Immutable State



Pure functions are those whose return values depend only upon the values of their arguments. Pure functions don't have side effects like network or database calls. Pure functions also do not override the values of anything. In the above example, a new array is returned instead of modifying the items that was passed in.

#### Avoiding Array Mutations <a id="avoiding-array-mutations"></a>

Suppose that in the state we have a key named `users` to store a user list. The user list is a Javascript Array of Javascript Objects, like:

```text
[
  {id: 1, name: 'a'},
  {id: 2, name: 'b'},
  {id: 3, name: 'c'},
  {id: 4, name: 'd'},
  {id: 5, name: 'e'},
];
```

Then we define a reducer function, return new state based on different actions:

```text
const reducer = (state = [], action) => {
  switch (action.type) {
    case 'ADD':
      return state.push(action.user);
    ...
  }
}

reducer([], {type: 'ADD', user: {id: 1, name: 'a'}});
```

Why this won't work?

Pure functions also do not override the values of anything. In this case, `state.push()` will override the old state.

Instead:

```text
const reducer = (state = [], action) => {
  switch (action.type) {
    case 'ADD':
      return [...state, {action.user}]
    ...
  }
}
```

Then think about how to perform a `DELETE`:

```text
const initState = [
  {id: 1, name: 'a'},
  {id: 2, name: 'b'},
  {id: 3, name: 'c'},
  {id: 4, name: 'd'},
  {id: 5, name: 'e'},
];
const reducer = (state = initState, action) => {
  const index = action.index;
  switch (action.type) {
    case 'DELETE':
      // wrong way
      return state.splice(index, 1);
      // right way
      return [...state.slice(0, index), ...state(index + 1)];
    ...
  }
}

reducer(initState, {type: 'DELETE', index: 2});
```

Then think about how to perform a `UPDATE`:

```text
const initState = [
  {id: 1, name: 'a'},
  {id: 2, name: 'b'},
  {id: 3, name: 'c'},
  {id: 4, name: 'd'},
  {id: 5, name: 'e'},
];
const reducer = (state = initState, action) => {
  const {index, user} = action;
  switch (action.type) {
    case 'UPDATE':
      return [
        ...state.slice(0, index),
        user,
        ...state.slice(index + 1)
      ];
    ...
  }
}

reducer(initState, {type: 'UPDATE', user: {id: 3, name: 'ddd'}});
```

#### Avoiding Object Mutations <a id="avoiding-object-mutations"></a>

Like the examples about how we return a new Array based on the old Array, we also need to know how to change an Object based on the old Object. Suppose we have:

```text
const initState = {
  id: 1,
  name: 'a',
  isAdmin: false
};
const reducer = (state = initState, action) => {
  switch (action.type) {
    case 'SWITCH_ADMIN':
      return {
        ...state,
        isAdmin: !state.isAdmin
      }
    ...
  }
}
reducer(initState, {type: 'SWITCH_ADMIN'});
```

##  

  


\*\*\*\*

\*\*\*\*

