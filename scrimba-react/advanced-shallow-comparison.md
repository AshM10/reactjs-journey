# What is "Shallow Comparison"?

- many of the optimizations you can do in react will require a good understanding on how react renders its components. 
- the two ways that react provides to us to increase its performance, both are going to require a good understanding of the concept of **Shallow Comparison** .
- In React, a shallow comparison is a way to compare two values to determine if they are the same. This type of comparison only looks at the top level of the values being compared and does not delve into the nested structure of the values.
- To perform a shallow comparison in React, you can use the shallowEqual function from the react-dom/test-utils module. This function takes two arguments and returns true if the values are the same, and false if they are different.
- Here is an example of how you might use the shallowEqual function:

```js
import { shallowEqual } from 'react-dom/test-utils';

const a = { foo: 'bar' };
const b = { foo: 'bar' };
const c = { foo: 'baz' };

console.log(shallowEqual(a, b)); // true
console.log(shallowEqual(a, c)); // false
```

- It's important to note that the shallowEqual function is intended for testing purposes and is not intended for use in production code. In production code, you should use the Object.is function or the triple-equals operator (===) to perform shallow comparisons.

## Strict Equal Operator

- The strictly equal operator (===) is a comparison operator in JavaScript that compares two values to determine if they are the same. It is also known as the triple-equals operator.
- The === operator compares values using the following rules:

1. If the two values are the same value, it returns true. This includes cases where the values are undefined, null, true, or false.
2. If the two values are numbers, it returns true if they are the same value, and false if they are not. This includes special values like NaN and +0 and -0.
3. If the two values are strings, it returns true if they are the same value, and false if they are not.
4. If the two values are objects, it returns true if they refer to the same object, and false if they do not.

- Here is an example of how you might use the === operator:

```js
console.log(1 === 1); // true
console.log(NaN === NaN); // false
console.log(+0 === -0); // true
console.log('foo' === 'foo'); // true
console.log([1, 2, 3] === [1, 2, 3]); // false

const a = {};
const b = a;
console.log(a === b); // true

```

### Examples

```js
// ===
// Primitive types (strings, numbers, booleans)
console.log("Hi" === "Hi") // true

// Complex types (array, object)
console.log({} === {}) // false
console.log({name: "Joe"} === {name: "Joe"}) // false, obj are not considered strictly equal to each other, obj are passed by reference instead of value

// Shallow comparison
const state = {
    favNumber: 42,
    name: "Bob",
    address: {
        street: "123 Main Street",
        city: "Nowhere, PA",
        zip: 12345
    }
}

const state2 = {
    favNumber: 42,
    name: "Bob",
    address: {
        street: "123 Main Street",
        city: "Nowhere, PA",
        zip: 12345
    }
}

console.log(state.favNumber === state2.favNumber) // true
console.log(state.name === state2.name) // true, because both their shallow properties are equal to each other
console.log(state.address === state2.address) // false, two obj defined in separate places are not gonna be considered shallow equal
```

```js
const person = {
    name: "Sarah"
}

const anotherPerson = person

console.log(anotherPerson === person) // true 
```

```js
const person = {
    name: "Sarah"
}

const anotherPerson = {
    name: "Sarah"
}

console.log(anotherPerson === person) // false
```

```js
const arr1 = [1, 2, 3]
const arr2 = [1, 2, 3]

arr1 === arr2 // false
```

## Resource

- [Comparison in React Docs](https://beta.reactjs.org/reference/react/memo#specifying-a-custom-comparison-function)

## Summary 

- In React, a shallow comparison is a comparison of two objects or values that only checks if they are the same object, rather than checking if they have the same properties and values. This is done using the Object.is function, which compares the two objects by their references rather than by their contents.

- Here's an example of a shallow comparison in React:

```js
import React from 'react';

function MyComponent(props) {
  const { value } = props;

  // Perform a shallow comparison of the value prop
  if (value !== prevValue) {
    // Do something if the value prop has changed
  }

  return <div>{value}</div>;
}
```

- In this example, the component only checks if the value prop has changed by comparing it to the previous value using the strict inequality operator (!==). If the two values are different objects with the same contents, the comparison will return false, even though the values are effectively equal.

- In contrast, a "deep" comparison would check if the two objects have the same properties and values, rather than just checking if they are the same object. This can be useful when comparing objects that may have nested properties or arrays.

