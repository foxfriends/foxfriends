# Node.js

[Node.js][] is an implementation of @[Javascript][] that is run outside of the @[browser][].
Due to Javascript's original usage for @[frontend][frontend-web] @[web development][],
Node.js was created to allow the use of Javascript also for the @[backend][backend-web],
making it easier for frontend developers to become @[full-stack][full-stack-development]
developers.

In addition to taking Javascript outside of the browser, Node.js came with @[NPM][], making
sharing and reusing Javascript code more accessible.

[Node.js]: https://nodejs.org

Though it can be used for any sort of application, Node.js is most often used for web servers
using a number of popular NPM packages, such as @[Koa][npm-koa] or @[Express][npm-express].

Similar projects include @[Deno][], currently in relatively early stages, which appears to
try and succeed Node.js by providing first-class support for @[TypeScript][] and changing
how the @[module][modules] system works. I am interested to see where this goes.

While Node.js is popular for and easy to use to create web servers, keep in mind that
it does not tend to lead to the most performant of programs. Though good for creating
prototypes quickly, for large-scale applications Node.js may not hold up and a more
powerful solution may be required.
