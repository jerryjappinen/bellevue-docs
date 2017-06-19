
# Setup and requirements

Scaffolding a new project with Bellevue is very easy: clone the repository, remove everything you don't need and start writing your global styles, services, models and components.

**Note:** This project template is **not** a component library. While many components are included out of the box, Bellevue is intended as a starting point for your custom application. You can choose to write your own components or import any component library you wish as [vendor code](../app/vendor.md).

**Note:** This project template should **not** be used as a dependency. In any practical project, you will want to make minor adjustments to the tooling and your app code will deviate significantly from what's included in the template, so you should not expect to reliably pull updates from `bellevue` in the future.

## Requirements

1. The Node version defined in [`.nvmrc`](./.nvmrc)

The easiest way to manage node versions is using [nvm](https://github.com/creationix/nvm).

## Project setup

```sh
# Clone repo
git clone git@github.com:Eiskis/bellevue.git my-app
mkdir my-app

# Install dependencies
npm install
```

## Building and testing

```sh
# Serve with hot reload
npm run dev

# Serve with hot reload on a specific port
PORT=1234 npm run dev

# Build for production with minification
npm run build

# Build for production and view the bundle analyzer report
npm run build --report

# Run all linters
npm run lint

# Run unit tests
npm run unit

# Run e2e tests on standalone Chrome
npm run e2e

# Run e2e tests on Selenium (requires Java)
DRIVER=selenium npm run e2e

# Run all tests
npm run test

# Generate all docs
npm run docs
```

See all scripts in [`package.json`](https://github.com/Eiskis/bellevue/tree/master/package.json).
