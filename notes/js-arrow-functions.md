# Javascript: Arrow Functions

@[Javascript][]'s [arrow functions][] are a type of anonymous function which have 
slightly different semantics than regular @[functions][], in that they do not have a
@[receiver][function-receiver] and cannot be @[bound][js-bind].

[Arrow functions]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions

Due to their shortened syntax compared to regular function expressions, arrow functions are
commonly used as @[lambdas][].

Compare the following functions:

```javascript
function regular(...args) { console.log(this, ...args); }
const expression = function (...args) { console.log(this, ...args); }
const arrow =  (...args) => console.log(this, ...args);

regular.call('this', 'arg1', 'arg2');
expression.call('this', 'arg1', 'arg2');
arrow.call('this', 'arg1', 'arg2');
```

In this situation, both the `regular` and `expression` version of the function
behave the same way (printing `this arg1 arg2`), but since the arrow function
cannot be bound to a receiver, the call to `arrow` prints `undefined arg1 arg2`.

Also worth noting is that, while arrow functions can be @[`async`][async-await],
they cannot be used as @[generators][generator-function].
