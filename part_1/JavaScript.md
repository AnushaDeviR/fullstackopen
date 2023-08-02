# JavaScript

- Standard name of JS is ECMAScript which is currently on the version ES14, but many browsers don't support them hence we need to transpile the code to older version supported by the browsers.
- Babel: a popular trans-compiler, automatically configured in React when created with `create-react-app`.
- NodeJs - a JS runtime environment which is based on Chrome's V8 JS engine. The latest Node version doesn't need to be trans-compiled since it can understand the latest version of JS.

## Variables

```javascript
const x = 1;
let y = 5;

y += 10;
console.log(x, y); // prints 1, 15

x = 2;
console.log(x, y); // causes error since the const does not define a variable instead it defines a constant where the value cannot be changed
```

### var keyword

```javascript
function varPrint() {
  for (var i = 0; i < 10; i++) {
    console.log(i);
  }
  console.log(i); // this would still print the number 10 since the scope of the variable is within the function
}
```

```javascript
function varPrint() {
  for (var i = 0; i < 10; i++) {
    console.log(i);
  }
}
varPrint();
console.log(i); // this would cause an error stating undefined since `i` is logged outside the function
```

### let keyword

```javascript
function varPrint() {
  for (let i = 0; i < 10; i++) {
    console.log(i); // prints the numbers
  }
  console.log(i); // this would cause a reference error since the variable is being called outside of its function scope
}
```

### const keyword

- Used to declare a variable that is constant (won't be changing)

```javascript
const dog = {
  age: 3,
};
dog.age = 5;
dog = { name: "biko" }; // this would throw an error since the object `dog` cannot be assigned with another variable than age
```
