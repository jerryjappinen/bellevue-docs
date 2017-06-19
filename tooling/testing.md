
# Testing

## Unit tests

```
test/
	└── unit/
		├── coverage/
		.	└── lcov-report/
		.		└── index.html
		└── specs/
			├──  components/
			├──  models/
			└── store/
```

Automated unit tests run on [Karma](https://karma-runner.github.io/1.0/index.html) and [Mocha](https://mochajs.org/), and are written using [Chai](http://chaijs.com/). Unit tests can be written for all the elements of application code, meaning services, models, components and utilities as well as Vuex code.

Running unit tests on the command line gives you a report like this:

![Unit test results on command line](../images/unit-test-report-cli.png)

The test pipeline will also generate an HTML report, which looks like this:

![Unit test results in HTML](../images/unit-test-report-html.png)

The HTML report will be available under  `/test/unit/coverage/lcov-report/`. You can open it over `file://`, no file server is needed.

## End-to-end tests

```
test/
	└── e2e/
		├──  custom-assertions/
		└── specs/
```

Automated end-to-end tests are written using [Nightwatch.js](http://nightwatchjs.org/). By default they are run on Chrome, which has a [standalone driver](https://sites.google.com/a/chromium.org/chromedriver/) that doesn't have dependencies.

When running the tests, you will see test report in your CLI that looks like this:

![End-to-end test results on command line](../images/e2e-test-report-cli.png)

### Selenium

If you want to run the tests via Selenium, which supports more browsers, `Java SE Development Kit` is required. You can download the latest JDK for your platform on [Oracle's download page](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).
