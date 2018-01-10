
# Feature comparison

Bellevue is built on top of the awesome, official [`vuejs-templates/webpack`](https://github.com/vuejs-templates/webpack) template. While it's a great template, it does lack a few features in the tooling, and provides very little in terms of architecture and patterns for writing application code on top of the tooling.

This project aims to provide a more realistic representation of what a modern full-featured frontend project will have. It's important to remember that there are many different, valid ways of introducing the features listed below, and any project template like this will have to make opinionated decisions about how to architecture everything. If you are unhappy with the way this project is structured, you can still use this comparison as a reference.

For a quick overview of what the full feature set of Bellevue is, check out the [annotated project structure](../overview/source.md).

## From `vuejs-templates/webpack`

|Feature|Bellevue|`vuejs-templates/webpack`
| -- | -- | -- |
|ES6|Yes|Yes
|Webpack 2|Yes|Yes
|Environment-specific tooling configuration|Yes|Yes
|URL resolution for all file types and assets|Yes|Yes
|Completely static assets|Yes|Yes
|Single-file components as `.vue` files|Yes|Yes
|Hot reload|Per-module|Per-module
|Minify and compile JS and CSS|Yes|Yes
|Autoprefixing for CSS|Yes|Yes
|Source maps|Yes|Yes
|Unit tests|[Jest](../tests/unit.md)|Jest
|E2E tests|[Selenium](../tests/e2e.md)|Selenium
|Routing with `vue-router`|[Yes](../ui/routing.md)|Yes
|Excellent error reporting|Yes|Yes



## New and improved

#### Preconfigured aliases

All relevant parts of your source code are preconfigured in Webpack, allowing you to avoid relative paths in your files.

#### Centralised config for tooling and app code

[Yes](../app/config.md)

#### SCSS

Supported in `.scss` files (global styles), `.vue` files (component styles). Sass variables are also exposed to JavaScript, avoiding duplication.

Includes many commonly used mixins, and separation between shared Sass tooling and global CSS.

#### Linting for `.js` and `.vue` files

Supported for `.js`, `.vue`, `.css` and `.scss` files. Additional linting configuration for JS imports, Vue-specific code styling (template, script and style) and Jest spec files.

#### Workspace configuration

Preconfigured settings for VS Code, common plugins, all linting tools, Babel etc.

#### SVG optimisation

Optimized with SVGO, and compiled to Vue components. Supports outputting SVGs with `currentColor` for CSS-based coloring.

[Read more)](../tooling/svg-compilation.md)

#### Preconfigured web font loading

[Yes](https://github.com/Eiskis/bellevue/tree/master/src/styles/webfonts)

#### Manifest files and meta tags

- Sitemap generation (`sitemap.xml`)
- `robots.txt` and robots meta tags
- WebApp `manifest.json` generation
- HTML meta tags: site-wide, prerendered

See [FAQ/meta](../faq/meta.md) for more information.

#### HTML meta tags: per route, run-time

[Yes, preconfigured](../faq/meta.md) (`vue-meta`)

#### Localisation capability

[Yes, preconfigured](../ui/localisation.md) (`vue-i18n`)

#### Centralised registration of Vue plugins

[Yes](https://github.com/Eiskis/bellevue/tree/master/src/vendor/vue.js)

#### Centralised registration of Vue components

[Yes](https://github.com/Eiskis/bellevue/tree/master/src/vendor/vue.js)

#### Centralised registration of Vue directives

[Yes](https://github.com/Eiskis/bellevue/tree/master/src/vendor/vue.js)

#### Centralised registration of Vue mixins

[Yes](https://github.com/Eiskis/bellevue/tree/master/src/vendor/vue.js)

#### Global stylesheet architecture

[Yes](../stylesheets/stylesheet/architecture.md)

#### App code: services

[Yes](https://github.com/Eiskis/bellevue/tree/master/src/services)

#### App code: business logic models

[Yes](https://github.com/Eiskis/bellevue/tree/master/src/models)

#### App code: custom utilities

[Yes](https://github.com/Eiskis/bellevue/tree/master/src/utilities)

#### Peristence

[Yes](../ui/persistence.md)

#### Vuex

[Yes, preconfigured](../app/vuex.md)

#### Server-side rendering

[Not preconfigured](../ui/ssr.md)

#### Offline support

Webpack's offline plugin `comes preconfigured`.

[Read more about offline](../ui/offline.md)

#### Google Analytics

Preconfigured (disabled by default)
