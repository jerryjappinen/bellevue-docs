
# Feature comparison

Bellevue is built on top of the awesome, official [`vuejs-templates/webpack`](https://github.com/vuejs-templates/webpack) template. While it's a great template, it does lack a few features in the tooling, and provides very little in terms of architecture and patterns for writing application code on top of the tooling.

This project aims to provide a more realistic representation of what a modern full-featured frontend project will have. It's important to remember that there are many different, valid ways of introducing the features listed below, and any project template like this will have to make opinionated decisions about how to architecture everything. If you are unhappy with the way this project is structured, you can still use this comparison as a reference.

For a quick overview of what the full feature set of Bellevue is, check out the [annotated project structure](project-structure.md).

## Tooling

|Feature|Bellevue|`vuejs-templates/webpack`
| -- | -- | -- |
|ES6|Yes|Yes
|Webpack 2|Yes|Yes
|Environment-specific tooling configuration|Yes|Yes
|URL resolution for all file types and assets|Yes|Yes
|Completely static assets|Yes|Yes
|Single-file components as `.vue` files|Yes|Yes
|Hot reload|Per-module|Per-module
|Asset minification and compilation|Yes|Yes
|Source maps|Yes|Yes
|Unit tests|[Yes](../tooling/testing.md) (crude and iffy)|Yes (crude and iffy)
|E2E tests|[Selenium or standalone Chrome](../tooling/testing.md)|Selenium
|Excellent error reporting|Yes|Yes
|Preconfigured aliases|More|Some
|Centralised config for tooling and app code|[Yes](../app/config.md)|-
|Autoprefixing for CSS|Yes|Yes
|SCSS support in `.scss` files|Yes|-
|SCSS support in `.vue` files|Yes|-
|JavaScript linting for `.js` and `.vue` files|Yes|Yes
|(S)CSS linting for `.css`, `.scss` and `.vue` files|Yes|-
|HTML linting for `.html` and `.vue` files|Yes|-
|Preconfigured linter rules with common plugins|Yes|-
|SVGO optimisation|Yes|-
|SVG tooling for setting currentColor|[Yes](../tooling/svg-compilation.md)|-
|SVG sprite compilation (including sample components)|Yes|-
|App icon (+ meta tag) generation|[Yes](../tooling/app-icons.md) (crude)|-
|Preconfigured web font loading|[Yes](https://github.com/Eiskis/bellevue/tree/master/src/styles/webfonts)|-
|Workspace configuration for Visual Studio Code|[Yes](https://github.com/Eiskis/bellevue/tree/master/.vscode/settings.json)|-
|Support for generated docs|[Yes](../tooling/docs.md) (crude)|-

## Application code

|Feature|Bellevue|`vuejs-templates/webpack`
| -- | -- | -- |
|Vue.js 2|Yes|Yes
|Routing with (`vue-router`)|[Yes](../ui/routing.md)|Yes
|Handling for HTML meta tags|[Yes, preconfigured](../ui/routing.md) (`vue-meta`)|-
|Localisation capability|[Yes, preconfigured](../ui/localisation.md) (`vue-i18n`)|-
|Centralised registration of Vue plugins|[Yes](https://github.com/Eiskis/bellevue/tree/master/src/main.js)|-
|Centralised registration of Vue components|[Yes](https://github.com/Eiskis/bellevue/tree/master/src/main.js)|-
|Centralised registration of Vue directives|[Yes](https://github.com/Eiskis/bellevue/tree/master/src/main.js)|-
|Centralised registration of Vue mixins|[Yes](https://github.com/Eiskis/bellevue/tree/master/src/main.js)|-
|Global stylesheet architecture|[Yes](../stylesheets/stylesheet/architecture.md)|-
|App code: services|[Yes](https://github.com/Eiskis/bellevue/tree/master/src/services)|-
|App code: business logic models|[Yes](https://github.com/Eiskis/bellevue/tree/master/src/models)|-
|App code: custom utilities|[Yes](https://github.com/Eiskis/bellevue/tree/master/src/utilities)|-
|Peristence|[Yes](../ui/persistence.md)|-
|Vuex|[Yes, preconfigured](../app/vuex.md)|-
|Server-side rendering|[Not preconfigured](../ui/ssr.md)|-
|Offline handling|[Limited (no manifests)](https://github.com/Eiskis/bellevue/tree/master/src/services/network.js)|-
|Authentication and authorization|[No](../ui/auth.md)|-
|Preconfigured form input validation|-|-

If you only need a subset of these features, the extra capabilities can easily be removed to stramline your app. Visit the corresponding section of the documentation for more information on how to remove specific features.

**Note:** this project is still early in development, and some features are implemented in a more mature form than others. If you choose to start from the official basic template, you will have to implement the missing features from scratch however.
