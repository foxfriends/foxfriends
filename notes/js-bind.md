# Javascript: Function Binding

One interesting, and unusual, feature of @[Javascript][] is the way @[functions][] behave
when used as @[methods][] (e.g. when called with a particular @[receiver][function-receiver]).
When a function is called this way, the receiver is available within that function's body as
`this`.

Consider the following example of a typical Javascript method declaration and invocation:

```javascript
class Hero {
    constructor(name) { this.name = name; }
    greet(greeting) { console.log(`${greeting} ${this.name}`); }
}

const link = new Hero('Link');
link.greet('Hello'); // logs "Hello Link"
```

Here, this works as you expect, and it logs the name of the `Hero`, "Link". When a function
is called directly on a value that contains that function as a member, the value that it
was called on is passed as the receiver, and all works as expected.

Things start to get weird when functions are detached from their instances:

```javascript
const showThatName = link.greet;
showThatName('Hello'); // Error!
```

Here, since we have taken the function out of the context of its value and then called it,
no value for `this` is passed, and we get an error: `Cannot read property 'name' of undefined`.
This happens because functions, by default, are *unbound*, and only get their receiver
based on context.

To get around this, we have a few options:
1.  Bind the `this` value to the function, using the `fn.bind()`
2.  Pass the `this` value explicitly at the time of calling, using either `fn.call()` or `fn.apply()`

```javascript
const showNameOfLink = link.greet.bind(link);
showNameOfLink('Hello'); // Ok: logs "Link"
showThatName.call(link, 'Hello'); // Ok: logs "Hello Link"
showThatName.apply(link, ['Hello']); // Ok: logs "Hello Link"
```

What else is interesting is that you can pass *any value* as the receiver of *any function*.

```javascript
let i = 0;
const fakeHero = { get name() { return ++i; } };
showThatName.call(fakeHero, 'Hello'); // Ok: logs "Hello 1"
showThatName.call(fakeHero, 'Hello'); // Ok: logs "Hello 2"
showThatName.call(fakeHero, 'Hello'); // Ok: logs "Hello 3"

function greetAnyone(greeting) {
    if (this instanceof Hero) {
        this.greet(greeting);
    } else {
        console.log(greeting);
    }
}
greetAnyone.call(link, 'Hello'); // Ok: logs "Hello Link"
greetAnyone('Hello'); // OK: logs "Hello"
```

When done unexpectedly, this can lead to some weird behaviours, so it is typically not
recommended to do things like that. There are times when it is done or can be useful
though.

Also worth noting is that @[arrow functions][js-arrow-functions] are functions that do
not have a receiver. Such functions are *always unbound*, and attempting to pass a
receiver to them via `bind`, `call` or `apply` has no effect. Instead, the `this` value
continues to refer to the `this` value at the time of creating the function:

```javascript
function greetDelayed(greeting) {
    return () => console.log(`${greeting} ${this.name}`);
}

const greet = greetDelayed.call(link, 'Hello');
greet(); // Ok: logs "Hello Link"
greet.call(null); // Ok: logs "Hello Link"
```
