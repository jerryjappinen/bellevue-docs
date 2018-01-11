
# End-to-end tests

```
e2e/                              // Spec files
	└── myTest.e2e.js
test/                             // Nightwatch configuration
	└── e2e/
		└── custom-assertions/
		└── reports/
```

End-to-end tests are written using [Nightwatch.js](http://nightwatchjs.org/). By default they run on Selenium, which requires Java, but this can be changed to a [standalone driver](http://nightwatchjs.org/gettingstarted#browser-drivers-setup).

Run the tests with the scripts listed in [setup instructions](../overview/setup.md). When running the tests, you will see report that looks like this:

![End-to-end test results on command line](../images/e2e-test-report-cli.png)

XML reports are also stored under `test/e2e/reports/`.

### Selenium

Selenium is also supported, as it supports more browsers, but to use the Selenium driver you must have `Java SE Development Kit` installed. You can download the latest JDK for your platform on [Oracle's download page](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

After installing JDK successfully, you can set `DRIVER=selenium` when running the `e2e` script, and the tests will be run on Selenium instead of standalone Chrome.
