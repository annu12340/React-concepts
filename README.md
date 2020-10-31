# React-concepts

### Index
1. Lifecycle of Components
2. Pure Components
3. React Memo 
4. React Refs 
5. Higher-Order Components
6. Error boundaries
7. Controlled components 
8. Synthetic events
     ...

I. React Router

II. Redux  


### Difference between 
1. Typescript and Javascript
2. Declarative vs Imperative Programming


## Interview Questions
A. https://github.com/sudheerj/reactjs-interview-questions
B. https://www.fullstack.cafe/blog/react-js-interview-questions

1. Why browsers cannot read JSX?
2. In ReactJS, why there is a need to capitalize on the components?

<hr/>

## Lifecycle of Components

Each component in React has a lifecycle which undergoes three phases : Mounting, Updating, and Unmounting.

React has four built-in methods that gets called, in this order, when mounting a component:

- constructor()  **/```useState( )```**
- getDerivedStateFromProps() **/ ```useEffect( ()=>{}, [prop1,prop2]  )```**
- render()
- componentDidMount()  **/```useEffect( ()=>{}, []  )```** :  runs only once, manly used to fetch data from an API 

A component is updated whenever there is a change in the component's state or props.React has five built-in methods that gets called, in this order, when a component is updated:

- getDerivedStateFromProps()
- shouldComponentUpdate() / **/```useMemo()```**
- render()
- getSnapshotBeforeUpdate()  **/```custom hooks```**
- componentDidUpdate()  **/```useEffect( ()=>{} )```** runs everytime there is a re-render

React has only one built-in method that gets called when a component is unmounted:
- componentWillUnmount()  **/```useEffect(() => { return () => {},  [])```**

<img src="https://pbs.twimg.com/media/DZ-97vzW4AAbcZj.jpg:large">

React hooks lifecycle 

<img src="https://raw.githubusercontent.com/Wavez/react-hooks-lifecycle/master/screenshot.jpg">

## Pure Components

Generally we use state or props value to decide the update cycle. React has now provided us a PureComponent which does the comparison of state and props to decide the update cycle.
Pure Components in React are the components which do not re-renders when the value of state and props has been updated with the same values. If the value of the previous state or props and the new state or props is the same, the component is not re-rendered This helps in improving the performance of the application

## React Memo

Memoizing in React is a performance feature of the framework that aims to speed up the render process of components. The memo part in React.memo is a derivative from memoization.
```
In computing, memoization or memoisation is an optimization technique used primarily to speed up computer programs by storing the results of expensive function calls and returning the cached result when the same inputs occur again
```

It’s a technique that executes a (pure) function once, saves the result in memory, and if we try to execute that function again with the same arguments as before, it just returns that previously saved result without executing the function again. And that kinda makes sense, doesn’t it? If the arguments are the same as last time, the outcome will be the same as well. So no need to execute that whole damn piece of code again.

It works kind of similar to Pure Component. The difference is that pure componenets works only with classes and it does only shallow comparsion

## React Refs 

In React, you generally should not be writing code that imperatively manipulates the DOM, but there are some situations where it’s necessary to do so. Refs exist, for just such occasions.
Refs provide a way access and manipulate DOM nodes and React elements , directly.

According to the docs, you should consider using refs when you need to:
- Manage focus, text selection, or media playback.
- Perform imperative animations.
- Integrate with third-party DOM libraries.

```Reference : https://medium.com/@mrewusi/a-gentle-introduction-to-refs-in-react-f407101a5ea6```

## Higher-Order Components

Higher-order components (HOCs) in React were inspired by higher-order functions in JavaScript. A higher-order component (HOC) is an advanced element for reusing logic in React components. Components take one or more components as arguments, and return a new upgraded component. Sounds familiar, right? They are similar to higher-order functions, which take some functions as an argument and produce a new function.
Higher order components are JavaScript functions used for adding additional functionalities to the existing component. HOC is wrapping around "normal" component and provide additional data input. It is actually a function that takes one component and returns another component that wraps the original one.

**Structure Of A Higher-Order Component**

```js
const NewComponent = (BaseComponent) => {
  // ... create new component from old one and update
  return UpdatedComponent
}
```
A HOC is structured like a higher-order function:

- It is a component.
- It takes another component as an argument.
- Then, it returns a new component.
- The component it returns can render the original component that was passed to it.

``` js
import React from 'react';
// Take in a component as argument WrappedComponent
const higherOrderComponent = (WrappedComponent) => {
// And return another component
  class HOC extends React.Component {
    render() {
      return <WrappedComponent />;
    }
  }
  return HOC;
};
```

We can see that higherOrderComponent takes a component (WrappedComponent) and returns another component inside of it. With this technique, whenever we need to reuse a particular component’s logic for something, we can create a HOC out of that component and use it wherever we like.

```Reference : https://www.smashingmagazine.com/2020/06/higher-order-components-react/```

```https://blog.jakoblind.no/simple-explanation-of-higher-order-components-hoc/```

## Error Boundaries
Error boundaries are React components that catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of the component tree that crashed. Error boundaries catch errors during rendering, in lifecycle methods, and in constructors of the whole tree below them.

- Only a class component can be used as an error boundary.
A class component becomes an error boundary if it defines either (or both) of the lifecycle methods static getDerivedStateFromError() or componentDidCatch().

```Reference : https://www.digitalocean.com/community/tutorials/react-error-boundaries```

```https://www.smashingmagazine.com/2020/06/react-error-handling-reporting-error-boundary-sentry/```


## Controlled components 

There are components in the ReactJS that maintain their own internal state. They are basically considered as uncontrolled components. On the other side, the components which don’t maintain any internal state are considered as controlled components in ReactJS. Controlled components can easily be controlled by several methods. Most of the React components are controlled components.

In HTML, form elements such as <input>, <textarea>, and <select> typically maintain their own state and update it based on user input. When a user submits a form the values from the aforementioned elements are sent with the form. With React it works differently. The component containing the form will keep track of the value of the input in it's state and will re-render the component each time the callback function e.g. onChange is fired as the state will be updated. A form element whose value is controlled by React in this way is called a "controlled component".
With a controlled component, every state mutation will have an associated handler function. This makes it straightforward to modify or validate user input.
 
- A Controlled Component is one that takes its current value through props and notifies changes through callbacks like onChange. A parent component “controls” it by handling the callback and managing its own state and passing the new values as props to the controlled component. You could also call this a “dumb component”.
- A Uncontrolled Component is one that stores its own state internally, and you query the DOM using a ref to find its current value when you need it. This is a bit more like traditional HTML.

##  Synthetic events

```Refer : https://radiant-brushlands-42789.herokuapp.com/medium.com/better-programming/an-intro-to-events-in-react-47a6a621b031```
React makes use of its own event system to provide cross-browser compatibility. To do this, React wraps native browser events in its own structure called a SyntheticEvent and passes them to React event handlers.

<br/>

<br/ >

## React Router

```Refer :https://blog.pshrmn.com/simple-react-router-v4-tutorial/,    https://www.freecodecamp.org/news/react-router-in-5-minutes/```

- When starting a new project, you need to determine which type of router to use. For browser based projects, there are <BrowserRouter> and <HashRouter> components.

```js
  import { BrowserRouter } from 'react-router-dom';

ReactDOM.render((
  <BrowserRouter>
    <App />
  </BrowserRouter>
), document.getElementById('root'));
```
- The <Route> component is the main building block of React Router. Anywhere that you want to only render content based on the location’s pathname, you should use a <Route> element. A <Route> expects a path prop, which is a string that describes the pathname that the route matches — for example, <Route path='/home'/> should match a pathname that begins with /roster  When the current location’s pathname is matched by the path, the route will render a React element. When the path does not match, the route will not render anything 
  
```
  <Switch>
  <Route exact path='/' component={Home}/>
  {/* both /roster and /roster/:number begin with /roster */}
  <Route path='/roster' component={Roster}/>
  <Route path='/schedule' component={Schedule}/>
</Switch>
 ```
- So far, our site is only navigable by typing the URLs. To add clickable links to the site, we use the Link element from React Router. Now add a Link for each component in the app and use to="URL" to link them.

```
function Navbar() {
  return (
    <div>
      <Link to="/">Home </Link>
      <Link to="/about">About Us </Link>
      <Link to="/shop">Shop Now </Link>
    </div>
  );
};
```

<br/>

<br/ >

## Redux

Redux is a js library that can be used with any js framework (not specific to react)

Redux is used mostly for application state management. An application state is like a global object which holds information that you use for various purposes later in the app (e.g. making decisions on which components to render and when, rendering the stored data etc).To summarize it, Redux maintains the state of an entire application in a single immutable state tree (object), which can’t be changed directly. When something changes, a new object is created (using actions and reducers). 

![Screenshot1](https://user-images.githubusercontent.com/43414928/97773801-dea03980-1b78-11eb-9388-d6604ee37b9e.png)
The left diagram represents a regular React app without Redux. Each circle represents a component.

When a component initiates a change (the blue circle), this change is communicated to the other components one step at a time. This may seem simple enough when we only have 10 components, but what about an app with 20, 50 or 100 components? As an app becomes larger, debugging can quickly become tricky, as we lose sight of how information is passed from one component to another.

On the right is the same React app with Redux. This time, when a component initiates a change, that information goes straight from it (the blue circle) to our store (the green circle). From there, the change is then communicated directly to all the components that need to update.

Redux, therefore, makes it much easier to diagnose problems: a problem will either be in the component that initiated the change (the blue circle) or in the code related to Redux itself.


### Redux Flow

``` Refer :  https://radiant-brushlands-42789.herokuapp.com/medium.com/@bretcameron/a-beginners-guide-to-redux-with-react-50309ae09a14 ```

![flow](https://miro.medium.com/max/1400/1*Pev6ubOxh74kOwh_fbEwVg.png)


#### Step 1: UI (User Interface)
This is where a change is triggered. For example, a user clicking a ‘+’ button in a simple counter app.

#### Step 2: Actions
The actual action/command we want to take place, for example, “add one”. In Redux, actions are plain JavaScript objects, and they must have a type property (e.g. 'ADD_ONE' ).

####  Step 3: Reducer
These specify how the application’s state should change in response to each action. For example, our new state should be one integer higher than our old state. 

#### Step 4A: Store
The store brings everything together. It holds application state, and it is where you will find three critical methods:

- getState() — which allows access to the state object
- dispatch(action) — which allows state to be updated
- subscribe(listener) — which registers listeners, allowing code to trigger every time a change takes place

#### Step 4B: State
Finally, state is contained within the store. It is an object that represents the dynamic parts of the app: anything that may change on the client-side.

In our example of a counter app, the state object will contain whatever number our counter is on. This change is then communicated back to the UI, where it will appear to the user.


### Redux has three building parts: 

```Refer : https://radiant-brushlands-42789.herokuapp.com/medium.com/javascript-in-plain-english/the-only-introduction-to-redux-and-react-redux-youll-ever-need-8ce5da9e53c6```
- actions
- store 
- reducers.
![](https://miro.medium.com/max/1400/1*CyLgf2qDp28sM6lr5g0q8Q.png)

A. Action
Actions are plain JavaScript objects that describe WHAT happened, but don’t describe HOW the app state changes.We just dispatch (send) them to our store instance whenever we want to update the state of our application. The rest is handled by the reducers, which we will familiarize ourselves with in just a moment

B. Store
The store hold the state of the application. One pattern that Redux follows is called “Single Source Of Truth”, which means that we have only one place (called Store) where we store the only state for the whole application.
In other words, one app — one store — one state. The store is actually an object, not a class. It contains a few extra things other than your application’s state as well (like functions and other objects

C. Reducers
Reducers are pure functions that define HOW the app state changes. In other words, they are used to recalculate the new application state or, at least a part of it.
Whenever we dispatch an action to our store, the action gets passed to the reducer.
The reducer function takes two parameters: the previous app state, the action being dispatched and returns the new app state.In other words, the reducer will calculate the new state of our app based on the action (and its type) we dispatched.


Let’s say that the user triggers an event (for example, clicks the “Add Note” button) and the app state updates (i.e. a new note is inserted into the app state). Here’s what happens under the hood:

1. The button click handler function dispatches an action to the store with the store.dispatch() method
2. Redux passes down the dispatched action to the reducer
3. The store saves the new state returned by the reducer
4. Since we have subscribed to the store, the function we provided will be called and it will update the UI accordingly (i.e., append the new note in the list of notes)

```Refer : https://www.smashingmagazine.com/2016/06/an-introduction-to-redux/```

![img2](https://cloud.netlifyusercontent.com/assets/344dbf88-fdf9-42bb-adb4-46f01eedd629/7912a5b9-bd10-4bc1-b3aa-23197aa12ddd/new-redux-data-flow-opt.png)

 <br/> <br/> <br/>
# Differences

### 1. Typescript vs Javascript

```Typescript = Js + other stuff```
Essentially, all your JavaScript code is also valid in Typescript – that means Typescript is a superset of JavaScript

TypeScript code is not understandable by the browsers. Thats why if the code is written in TypeScript then it is compiled and converted the code i.e. translate the code into JavaScript.The above process is known as Trans-piled. By the help of JavaScript code, browsers are able to read the code and display.
![Screenshot](https://user-images.githubusercontent.com/43414928/97773288-633c8900-1b74-11eb-94ad-2ee37528f010.png)


### 2.  Declarative vs Imperative Programming

Declarative Programming is like asking your friend to draw a landscape. You don’t care how they draw it, that’s up to them.
Imperative Programming is like your friend listening to Bob Ross tell them how to paint a landscape. While good ole Bob Ross isn’t exactly commanding, he is giving them step by step directions to get the desired result.

In an imperative world, we'd tell them to open the can of paint, dip their brush in it, and then move the brush in a stroking fashion along the wall. We'd be telling the painter exactly what to do.

In a declarative world, we would tell the painter "I want a house with a big ol' cartoon house horrendously smeared across the side of it...Oh! And I've had a tough week so make my day while doing it...", and she'd get it done! Why? Because the painter knows what to do! We don't need to tell her how to apply paint or how to get in and out of costume.

- Declarative programming focuses on the WHAT rather than the HOW. Declarative programming is much more driven by the result and describing this end result rather than the step by step process of getting to the result. This is opposed to imperative programming which is much more instructional and cares about the step by step process
- Declarative programming is a programming paradigm  that expresses the logic of a computation without describing its control flow. Imperative programming is a programming paradigm that uses statements that change a program’s state.
- 

Imperative example
```
const container = document.getElementById(‘container’);
const btn = document.createElement(‘button’);
btn.className = ‘btn red’;
btn.onclick = function(event) {
 if (this.classList.contains(‘red’)) {
   this.classList.remove(‘red’);
   this.classList.add(‘blue’);
 } else {
   this.classList.remove(‘blue’);
   this.classList.add(‘red’);
 }
};
container.appendChild(btn);
```

Declarative example
```
class Button extends React.Component{
  this.state = { color: 'red' }
  handleChange = () => {
    const color = this.state.color === 'red' ? 'blue' : 'red';
    this.setState({ color });
  }
  render() {
    return (<div>
      <button 
         className=`btn ${this.state.color}`
         onClick={this.handleChange}>
      </button>
    </div>);
  }
}

```



The differences here may be subtle. We still have logic that says if red then blue, but there’s one huge difference. The React example never actually touches an element. it simply declares an element should be rendered given our current state. It does not actually manipulate the DOM itself.
When writing React, it’s often good not to think of how you want to accomplish a result, but instead what the component should look like in it’s new state. This sets us up for a good control flow where state goes through a series of predictable and replicable mutations

<br/ >
<br/>

## Interview Questions

**Why browsers cannot read JSX?**

Actually, JSX is not considered as a proper JavaScript. Browsers cannot read them simply. There is always a need to compile the files that contain JavaScript Code. This is usually done with the help of JSX compiler which performs its task prior to file entering the browser. Also, compiling is not possible in every case. It depends on a lot of factors such as the source or nature of file or data.


**In ReactJS, why there is a need to capitalize on the components?**

It is necessary because components are not the DOM element but they are constructors. If they are not capitalized, they can cause various issues and can confuse developers with several elements. At the same time, the problem of integration of some elements and commands can be there.
