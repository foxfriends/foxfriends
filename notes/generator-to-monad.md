# Generator to Monad Transformation

One of the many applications of @[generators][generator-function] is to implement
a (deterministic) version of the @[`do` notation][monad-do] in @[Javascript][] (or
really, in any @[language][programming-language] with generators and a way to 
represent @[monads][monad]).

```javascript
function do_(Monad, generator) {
    const next = (iter, input) => {
        const { value, done } = iter.next(input);
        if (done) { return Monad.of(value); }
        return value.bind((output) => next(iter, output));
    };
    return Monad.of(undefined).bind(() => next(generator(), undefined);
}
```

If immutable generators were a thing, it would be possible to implement the 
non-deterministic version as well. Consider a world where `inext()` (immutable-next)
returns `{ done, value, cont }`, expecting the next call to `inext()` is done
on the `cont`, instead of modifying the current value,

```javascript
function do_(Monad, generator) {
    const next = (iter, input) => {
        const { value, done, cont } = iter.inext(input);
        if (done) { return Monad.of(value); }
        return value.bind((output) => next(cont, output));
    };
    return Monad.of(undefined).bind(() => next(generator(), undefined);
}
```
