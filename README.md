## AtScript Playground

This is an empty repo to make it easy to experiment with [AtScript].
Please note that this is a fork of the original [AtScript Playground](github.com/angular/atscript-playground) by the Angular team.
It includes
* an updated [Traceur Version](https://github.com/google/traceur-compiler)
* a slightly modified [RTTS-Assert Version](https://github.com/stsc3000/assert)
  to support at least Array as a generic type
* a test suite to explain AtScript functionality

The repo was adjusted in conjunction with a yet to be linked blog post.

### Initial setup

```bash
# Clone the repo...
git clone https://github.com/zweitag/atscript-playground.git
cd atscript-playground

# Then, you need to install all the dependencies... (sudo if you need to)
npm install
```

### Getting Started
In order to start experimenting with AtScript, please
```bash
# Run Gulp to watch the src folder and start a server on port 8000
gulp
```
You may then experiment in `src/main.ats`. If you want source maps use
```bash
gulp --sourceMaps
```

You will find a set of tests for many of AtScript's features in the `test`
directory. In order to run the tests, please

```bash
# Run Gulp to watch and compile the tests
gulp
```

and in another shell

```bash
# Run the test suite
npm test
```
### What are all the pieces involved?

#### [Traceur]
Transpiles AtScript code into regular ES5 (today's JavaScript) so that it can be run in a current browser.

#### [RequireJS]
Traceur is configured to transpile AtScript modules into AMD syntax and we use RequireJS to load the code in the browser. This is just temporary until we improve the ES Module Loader polyfill ([more details](https://github.com/angular/atscript-playground/issues/3)).

#### [Assert] library
When `typeAssertions: true` option is used, Traceur generates run-time type assertions such as `assert.type(x, Object)`. The assert library does the actual run-time check. Of course, you can use your own assert library.

The idea with type assertions is that you only use them during the development/testing and when deploying, you use `typeAssertions: false`.

#### [Karma]
Test runner that runs the tests in specified browsers, every time that you change a file.

#### [Gulp]
Task runner to make defining and running the tasks simpler.


[AtScript]: http://atscript.org
[Traceur]: https://github.com/google/traceur-compiler
[RequireJS]: http://requirejs.org
[Assert]: https://github.com/angular/assert
[Karma]: http://karma-runner.github.io/
[Gulp]: http://gulpjs.com
