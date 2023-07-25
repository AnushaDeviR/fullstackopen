# Introduction to React

- Create a react project run: `npx create-react-app`.
- `npm start`: runs the application in localhost

## Component

The file `App.js` in `src` directory defines a React component with the name `App`, in which it is rendered by the `div` element in the index.js file. The `public/index.html` is the main HTML file that includes the React code and provides a context for React to render to. The id `root` mentioned in the index.js file refers to the div element's id in the public/index.html file.

```javascript
ReactDOM.createRoot(document.getElementById("root")).render(<App />);
```

<br>

The components created in React are defined as JavaScript functions that are assigned to a variable:

```javascript
() => (
  <div>
    <p>Hello world</p>
  </div>
);
```

- The above function is defined by an arrow function which returns the value of the expression.
- Dynamic contents can also be rendered within a component.

```javascript
const App = () => {
  const now = new Date();
  console.log(now);
  return (
    <div>
      <p>Hello World, it is {now.toString()}</p>
    </div>
  );
};

export default App;
```

- Any JS code within the curly brackets `{now.toString()}` are evaluated and the result is embedded into the desired component produced in HTML.

## JSX (JavaScript Syntax Extension)

- React components return HTML markups, but they are written mostly using JSX.
- JSX returns React components which are compiled into JavaScript.
- The application looks like the below code after compiling, which is handled by `Babel` (with `create-react-app`, it is configured to automatically compile the application):

```javascript
const App = () => {
  const now = new Date();
  return React.createElement(
    "div",
    null,
    React.createElement("p", null, "Hello world, it is ", now.toString())
  );
};
```

- JSX is XML-like where every HTML tags needs to be closed

## Multiple components

```javascript
const Hello = () => {
  return (
    <div>
      <p>Hello</p>
    </div>
  );
};
const App = () => {
  const now = new Date();
  console.log(now);
  return (
    <div>
      <Hello />
      <p>The time is {now.toString()}</p>
    </div>
  );
};

export default App;
```

- Many components can be created and rendered in various pages.
- The `App` is the root component, but there can be situations where it is not exactly the root component by is wrapped within an appropriate utility component.
