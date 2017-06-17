
# Setup and requirements

Scaffolding a new project with Bellevue is very easy: clone the repository, remove everything you don't need and start writing your global styles, services, models and components.

**Note:** This project template is **not** a component library. While many components are included out of the box, Bellevue is intended as a starting point for your custom application. You can choose to write your own components or import any component library you wish as [vendor code](../app/vendor.md).

**Note:** This project template should **not** be used as a dependency. In any practical project, you will want to make minor adjustments to the tooling and your app code will deviate significantly from what's included in the template, so you should not expect to reliably pull updates from `bellevue` in the future.

## Requirements

1. The Node version defined in [`.nvmrc`](./.nvmrc)

The easiest way to manage node versions is using [nvm](https://github.com/creationix/nvm).

## Project setup

``` bash
# install dependencies
npm install
```

## Building and testing

``` bash
# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm run test

# generate all docs
npm run docs

# run all linters
npm run lint
```

See all scripts in [`package.json`](./package.json).
