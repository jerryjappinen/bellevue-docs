
# End-to-end tests

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
