
# Setup and requirements

This template is **not** a component library. Similar to the official templates, it is intended as a starting point that provides a good deal of patterns and architectures for writing a complex application with custom application code. You can of course import any component library you choose, or write everything yourself, just like with any ES6 or Vue project.

This template is **not** suitable for use as a dependency. Similar to the official templates, when starting a new project with this template, you should clone it as a new project, clean it up (removing any elements you do not wish to use), and then start writing your custom global styles, services, models and components. You can do the cleanup either conservatively or heavy-handedly; either way, you should not expect to be able to reliably pull updates from `bellevue` - it would not be practical to maintain a project that would support this.

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
