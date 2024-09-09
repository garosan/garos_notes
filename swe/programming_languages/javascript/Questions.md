### ¿What is `'use strict'` in JavaScript?

_R. `'use strict'` is a directive introduced in ES5 (2009) that enforces stricter parsing and error handling. It can be enabled for the whole script or for a simple function. Some of its features are:_

- Eliminates Silent Errors
- Prevents Accidental Globals
- Disallows Duplicates
- Disables `this` for Global Objects

### Explain the keyword `this` in JavaScript

The keyword `this` refers to the context in which a function is executed. Its value can vary depending on how the function is called.

Common scenarios:

- In the global execution context (outside of any function), `this` refers to the global object. In a browser, the global object is `window`.
- Inside a function in non-strict mode, `this` refers to the global object (`window` in browsers).
- Inside a function in strict mode, `this` is `undefined`.
- Object Methods: When a method is called as part of an object, `this` refers to the object the method is called on:

```javascript
const person = {
  name: "John",
  greet: function () {
    console.log(this.name); // `this` refers to the `person` object
  },
};
person.greet(); // Output: "John"
```

Constructor Functions: When using a constructor function (with new), this refers to the newly created object.

```javascript
function Person(name) {
  this.name = name;
}
const person1 = new Person("Alice");
console.log(person1.name); // Output: "Alice"
```
