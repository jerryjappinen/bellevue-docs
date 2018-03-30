
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

#### Configuration

[Centralised config for tooling and app code](../app/config.md)

#### Stylesheets

Sass support is preconfigured for global styling (separate `.scss` files), and component styles (`.vue` files). Sass variables are also exposed to JavaScript, avoiding duplication. Included are commonly used mixins and other Sass tools that are shared across the application code.

[Read more](../app/stylesheets.md)

#### Assets and SVG optimisation
Centralised config for tooling and app code
Preconfigured support for using bitmap and other assets from one place without relative paths. SVG assets are compiled and optimized, and support `currentColor` for CSS-based coloring. Support for adding local web fonts is also preconfigured.

- [Using assets](../ui/assets.md)
- [SVG tooling](../tooling/svg-compilation.md)
- [Web fonts](../ui/webfonts.md)

#### Linting and workspace configuration

Linting is preconfigured for `.js`, `.vue`, `.css` and `.scss` files. Additional linting configuration for JS imports, Vue-specific code stylesheets (template, script and style) and Jest spec files. Linters can be run on command line or in your editor.

Preconfigured settings for VS Code (common plugins, all linting tools, Babel etc.).

#### Manifest files and meta tags

- Sitemap generation (`sitemap.xml`)
- `robots.txt` and robots meta tags
- WebApp `manifest.json` generation
- Advanced `index.html` templating (prerendered)
- Run-time meta tag management

[Read more](../tooling/meta.md)

#### Vue plugins

Support for the following comes preconfigured:

- Plugins
- Components
- Directives
- Filters
- Mixins

Each of these can be registered globally or imported per component. New plugins and other extensions can be added easily.

[Read more](https://github.com/Eiskis/bellevue/tree/master/src/vendor/vue.js)

#### App code structure

- [Services](https://github.com/Eiskis/bellevue/tree/master/src/services)
- [Models](https://github.com/Eiskis/bellevue/tree/master/src/models)
- [Utilities](https://github.com/Eiskis/bellevue/tree/master/src/utilities)

#### Persistence

Persistence can be achieved via preconfigured routing or local storage support. [Read more](../ui/persistence.md)

#### Vuex

Preconfigured Vuex with module support and tests. [Read more](../app/vuex.md)

#### Offline support

Webpack's offline plugin preconfigured (disabled by default). Included `network` service to detect network status in runtime code. [Read more](../app/offline.md)

#### Google Analytics

Preconfigured (disabled by default). [Read more](../app/analytics.md)



## Not preconfigured

- Localisation: [Read more](../ui/localisation.md)
- Server-side rendering: [Read more](../ui/ssr.md)
