
# Source code structure

[Browse source on GitHub](https://github.com/Eiskis/bellevue)

```
e2e/                                  // End-to-end tests (on Nightwatch)
	└── myTest.e2e.js
src/
	├── assets/                       // Generic asset files such as images
	├── components/                   // Views, single-file .vue components
	├── config/                       // All custom configuration for tooling and app code
	.	├── dev/                      // Config overrides for development mode
	.	.	├── config.dev.build.js
	.	.	├── config.dev.meta.js
	.	.	└── config.dev.paths.js
	.	├── tooling/                  // Configuration that won't be available runtime
	.	.	├── config.aliases.js     // Webpack aliases
	.	.	├── config.robotsTxt.js
	.	.	├── config.routes.js      // Routes
	.	.	└── config.sitemap.js
	.	├── config.build.js
	.	├── config.manifest.js
	.	├── config.meta.js            // Meta information (app title, description etc.)
	.	├── config.paths.js
	.	├── config.router.js
	.	├── config.styles.js
	.	├── config.svgo.js
	.	└── index.js
	├── directives/                   // Vue directives
	├── mixins/                       // Vue mixins (NOT Sass mixins)
	├── models/                       // JS business logic objects
	├── plugins/                      // Vue plugins
	├── services/                     // JS custom (reactive) services
	└── styles/                       // Global base styling and style utilities
	.	├── defaults/
	.	├── functions/
	.	├── keyframes/
	.	├── mixins/
	.	├── transitions/
	.	├── utilities/
	.	├── constants.scss            // SCSS variable sheet (also exported to JS)
	.	├── global.scss               // All global base styling
	.	├── normalize.scss
	.	└── shared.scss               // All SCSS constants and mixins (won't output CSS)
	├── svg/                          // SVG assets to optimize and compile
	├── util/                         // JS custom utilities
	├── vendor/                       // Vendor libraries setup
	├── index.html.ejs                // Main HTML template
	├── main.js                       // Vue setup and main entry point for client app
	├── stylelint.config.js           // Linter configuration
	├── .htmllintrc                   // Linter configuration
	└── .eslintrc.js                  // Linter configuration
static/                               // Static files to host alongside product, including app icons
	├── _redirects
	├── favicon.png
	├── icon-48.png
	└── ...
unit/                                 // Unit tests (on Jest)
	├── components/
	├── models/
	├── services/
	└── util/
		└── myUtilName.spec.js
```



## Tooling

```
build/                                // Webpack build scripts
config/                               // Environment configuration
test/
	├── e2e/                          // Nightwatch configuration
	.	└── custom-assertions/
	└── unit/                         // Jest configuration
		├── stubs/
		└── jest.conf.js
package.json                          // Dev and app dependencies, development scripts
.nvmrc                                // Node.js version
```

## Extras

```
.vscode/                              // Workspace settings for Visual Studio Code
```
