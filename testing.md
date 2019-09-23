# Testing

[Karma][0] is a JavaScript browser test-runner. It allows to run tests in multiple browsers using Karma launchers. There are also launchers for PhantomJS and [jsdom][2].

[PhantomJS][1] is a headless WebKit scriptable with a JavaScript API.

[Jest](https://jestjs.io) is the most popular testing tool by far today though.

## ROI of tests

In case of UI app, integration tests give developer much more confidence that it works as expected. It brings just a little bit more effort than unit tests. The result is that they have highest ROI.

[Lean Testing or Why Unit Tests are Worse than You Think](https://blog.usejournal.com/lean-testing-or-why-unit-tests-are-worse-than-you-think-b6500139a009)

Use [react-testing-library](https://github.com/testing-library/react-testing-library) to enforce best practices in integration tests.

[0]: https://karma-runner.github.io/1.0/index.html
[1]: http://phantomjs.org
[2]: https://github.com/tmpvar/jsdom