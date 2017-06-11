
# Production builds

In production builds, the Webpack pipeline will do a lot of things to bundle all the requires code and assets as efficiently as possible for production environments.

Among other things,

- HTML will be minified, and comments will be removed.
- CSS will be minified, and comments will be removed.
- JS will be minified and uglified, and comments will be removed.
- All static assets will be copied ofer to a the assets directory, and all related URLs resolved.

## Running the build scripts

To compile a bundle for production, simply use the following command:

```sh
npm run build
```

The build process will take a while, but once it's done, you will see a satisfying report in your terminal:

![Build report](../images/build-report.png)

You can also `npm run build --report` to get a more detailed report on your final bundle. At the end of the build, Webpack will open an inspectable graph in your browser that gives you a great overview of how your bundle breaks down.

![Detailed build report](../images/build-report-detailed.png)

This is a great way to get a better understanding of which libraries take up the lions' share of the bundle size, and where to optimize if your production builds are too big. This will also reveal any unintendedly included libraries.
