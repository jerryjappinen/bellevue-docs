
# Feature comparison

`Eiskis/vue-webpack` is built on top of the awesome, official [`vuejs-templates/webpack`](https://github.com/vuejs-templates/webpack) template. While it's a great template, it does lack a few features in the tooling, and provides very little in terms of architecture and patterns for writing application code on top of the pipeline setup.

This project aims to provide a more realistic representation of what a modern full-featured frontend project will have. It's important to remember that there are many different, valid ways of introducing the features listed below, and any project template like this will have to make opinionated decisions about how to architecture everything. If you are unhappy with the way this project is structured, you can still use this comparison as a reference.

For a quick overview of what the full feature set of `Eiskis/vue-webpack` is, check out the [annotated project structure](project-structure.md).

|Feature|`Eiskis/vue-webpack`|`vuejs-templates/webpack`
| -- | -- | -- |
|ES6|Yes|Yes
|Webpack 2|Yes|Yes
|URL resolution for all file types and all assets|Yes|Yes
|True static assets|Yes|Yes
|Hot reload|Per-module|Per-module
|Asset minification and compilation|Yes|Yes
|Production builds|Yes|Yes
|Unit and E2E tests|Yes (crude and iffy)|Yes (crude and iffy)
|Excellent error reporting|Yes|Yes
|JavaScript linting|Yes|Yes
|CSS linting|Yes|-
|SCSS linting|Yes|-
|HTML linting|Yes|-
|Preconfigured aliases|More|Some
|Preconfigured linter config and plugins|Yes|-
|SCSS support in `.scss` files|Yes|-
|SCSS support in `.scss` files|Yes|-
|SVG optimisation and sprite compilation (components included)|Yes|-
|App icon (+ meta tag) generation|[Yes](pipeline/app-icons.md) (crude)|-
|Preconfigured web font loading|[Yes](https://github.com/Eiskis/vue-webpack/tree/master/src/styles/webfonts)|-
|Global stylesheet architecture|[Yes](../stylesheets/stylesheet/architecture.md)|-
|Centralised config for tooling and app code|[Yes](https://github.com/Eiskis/vue-webpack/tree/master/src/config)|-
|Centralised registration of Vue plugins, components, directives and mixins|[Yes](https://github.com/Eiskis/vue-webpack/tree/master/src/main.js)|-
|Preconfigured routing|[Yes](ui/routing.md) (`vue-router`)|-
|Preconfigured localisation capability|[Yes](ui/localisation.md) (`vue-i18n`)|-
|Preconfigured Vuex|[Yes](app/vuex.md)|-
|App code architecture: services|[Yes](https://github.com/Eiskis/vue-webpack/tree/master/src/services)|-
|App code architecture: business logic models|[Yes](https://github.com/Eiskis/vue-webpack/tree/master/src/models)|-
|App code architecture: custom utilities|[Yes](https://github.com/Eiskis/vue-webpack/tree/master/src/utilities)|-
