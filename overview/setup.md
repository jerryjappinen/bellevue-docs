
# Setup and requirements

Scaffolding a new project with Bellevue is very easy: clone the repository, install dependencies, remove everything you don't need and start writing your global styles, services, models and components.

**Note:** This project template is **not** a component library. While some components are included out of the box, Bellevue is intended as a starting point for your custom application. You can choose to write your own components, or import any of the many component libraries you wish as [vendor code](../app/vendor.md).

**Note:** This project template should **not** be used as a dependency. In any practical project, you will want to make minor adjustments to the tooling and your app code will deviate significantly from what's included in the template, so you should not expect to reliably pull updates indefinitely from `bellevue` in the future.

## Requirements

1. The Node version defined in [.nvmrc](./nvmrc)

**Protip:** manage node versions easily with [nvm](https://github.com/creationix/nvm).

## Project setup

```sh
# Clone repo
git clone git@github.com:Eiskis/bellevue.git my-app
mkdir my-app

# Install dependencies
npm install
```

## Building and testing

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# serve with hot reload at custom port
PORT=1234 npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build:report

# run unit tests
npm run unit

# run unit tests and show coverage report
npm run unit:coverage

# run unit tests and with hot reload (`jest --watch`)
# NOTE: You have more options in the terminal after you run this command
# NOTE: You can change this to `--watchAll` in `package.json` in case of issues
# NOTE: See https://github.com/facebook/jest/issues/4883
npm run unit:watch

# run e2e tests
npm run e2e

# run all tests
npm test
```

See all scripts in [`package.json`](https://github.com/Eiskis/bellevue/tree/master/package.json).
