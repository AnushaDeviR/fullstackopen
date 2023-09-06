# Component state, event handlers

## Component helper functions

- Helper functions are defined within another functions that defines the behavior of the component.

```js
const Hello = (props) => {
  const birthYear = () => {
    const yearNow = new Date().getFullYear();
    return yearNow - props.age;
  };

  return (
    <>
      <p>
        Hello {props.name}, you are {props.age} years old.
      </p>
      <p>You are {bornYear()} now 🤓</p>
    </>
  );
};
```

- The above `birthYear` function is a component helper function, declaring this in Java can be complex, but it is a common practice in JavaScript.
- The user's age does not have to be passed as a parameter as it is directly accesses all props that are passed to the component.

## Destructuring

- Destructuring was added in the ES6 version of JavaScript.
- It unpacks values from arrays or properties from objects upon assignment. (Ref: [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment))
- From the example of components helper function (`birthYear()`), it can be noticed that `props.age` is being called twice in the function and in the return syntax. This can be written in a more compact way using destructuring.

```js
const Hello = (props) => {
  const name = props.name;
  const age = props.age;
  const birthYear = () => new Date().getFullYear() - age;

  return (
    <>
      <p>
        Hello {name}, you are {age} years old.
      </p>
      <p>You are {bornYear()} now 🤓</p>
    </>
  );
};
```

- Destructuring makes variable assignments easier to extract and gather values of an object's properties into separate variables.
- Alternative ways to destructure props in a function:

```js
const { name, age } = props;
// or
const Hello = ({ name, age }) => {
  // rest of the code
};
```

## Page re-rendering

```js
// App.js
const App = (props) => {
  const { counter } = props;
  return <>{counter}</>;
};
```

```js
// index.js
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

let counter = 1;

const refresh = () => {
  ReactDOM.createRoot(document.getElementById("root")).render(
    <App counter={counter} />
  );
};

refresh();
counter += 1;
refresh();
counter += 1;
refresh();
```

- When the counter updates/ increments after calling refresh(), the values 1,2 are being incremented, but the value 3 is displayed on the screen as values 1 and 2 are displayed but for a very short amount of time that they can't be noticed.

- Alternatively, the above re-rendering can also be written as:

```js
setInterval(() => {
  refresh();
  counter += 1;
}, 1000);
```

## Stateful component

- The examples above are all simple functions without the use of states.
- State in React refers to a component's memory, components often change results as per a result of user interactions and some components needs to remember the current or past results.
- This is accomplished using `useState` hook (Ref: [State: A Component's Memory](https://react.dev/learn/state-a-components-memory)) in React.
- States locally stores the results or details.

```js
import { useState } from "react"; // useState needs to be imported from react to utilize state management in components
() => {
  /*The function returns an array containing 2 variables using the destructuring syntax - counter and setCounter. 
  The counter variable is assigned to initial value (0) of the state. The setCounter is assigned to the function to modify the state.
  */
  const [counter, setCounter] = useState(0); //state is added to the component and renders it with the initial value 0

  setTimeout(() => setCounter(counter + 1), 1000); //the setTimeOut() uses the modifier state variable to indicate the re-rendering of the component

  console.log("rendering...", counter);

  return <div>{counter}</div>;
};
```

- The first time the `setTimeOut()` function is called, the function body of the component is executed with 1 sec. timeout; the second time it gets executed, it calls the `useState` function and returns the incremented new value in the state.
