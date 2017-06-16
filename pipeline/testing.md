
# Testing

## Unit tests

```
test/
	|_ unit/
		|_ specs/
			|_ components/
			|_ models/
			|_ store/
```

Automated unit tests run on [Karma](https://karma-runner.github.io/1.0/index.html) and [Mocha](https://mochajs.org/), and are written using [Chai](http://chaijs.com/). Unit tests can be written for all the elements of application code, meaning services, models, components and utilities as well as Vuex code.

## End-to-end tests

```
test/
	|_ e2e/
		|_ custom-assertions/
		|_ specs/
```

Automated end-to-end tests are written using [Nightwatch.js](http://nightwatchjs.org/) and run via Selenium.
