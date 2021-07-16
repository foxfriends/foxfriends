# Javascript: Generators

@[Javascript][] has language-level support for @[generators][generator-function]. Generators are defined
with the `function*` keyword and, when called, return an @[iterator][] that follows the 
[Iterator protocol][].

[Iterator protocol]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols

```javascript
// `upto` is a generator that generates numbers up to `n` from 0
function* upto(n) {
    for (let i = 0; i < n; ++i) yield i;
}

const iter = upto(3);
const nums = [...iter]; // [0, 1, 2]

const inf = upto(-1);
inf.next(); // { value: 0, done: false }
inf.next(); // { value: 1, done: false }
inf.next(); // { value: 2, done: false }
inf.next(); // { value: 3, done: false }
inf.next(); // { value: 4, done: false }
// ... this could go on forever
```
