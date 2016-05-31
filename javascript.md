# JavaScript

Use term [Universal JavaScript](https://medium.com/@mjackson/universal-javascript-4761051b7ae9#.kcd19ajvv) instead of Isomorphic JavaScript.

Naming changes of ES standard: Harmony → ES6 → ES2015

**Pure function** is a function where the return value is only determined by its input values, without observable side effects. That means no API calls, route transitions, arguments mutation or calling non-pure functions like `Date.now()` or `Math.random()`. Pure function always returns the same value for any given input.

[**Higher order function**](http://www.sitepoint.com/higher-order-functions-javascript/) is a function that can take another function as an argument, or that returns a function as a result.

Grunt, Gulp, Browserify and Webpack were created as developers recognized the benefits of using Node for **tooling and dependency management**.