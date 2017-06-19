
# Source code structure

[Browse source on GitHub](https://github.com/Eiskis/bellevue)

```
docs/                                // Documentation generated from codebase
src/
	├── app-icon/                     // App icon assets
	├── assets/                       // Generic asset files such as images
	├── components/                   // Views, single-file .vue components
	└── config/                       // Custom configuration for tooling and app code
		├── config.aliases.js
		├── config.base.js
		└── config.routes.js
	├── fonts/                        // Web font assets
	├── locales/                      // Localisation files (per-language messages and formats)
	├── models/                       // JS business logic objects
	├── services/                     // JS custom (reactive) services
	├── store/                        // JS state management code
	└── styles/                       // Global base styling and style utilities
		├── base/
		├── definitions/
		├── keyframes/
		├── mixins/
		├── normalize/
		├── toolchain/
		├── transitions/
		├── utilities-base/
		├── utilities-composed/
		├── vendor/
		├── vendor-overrides/
		├── webfonts/
		├── global.scss               // All global base styling
		├── shared.scss               // All SCSS constants and mixins
		├── utilities.scss            // All global CSS utilities
	├── svg/                          // SVG assets that will be compiled into a sprite
	├── util/                         // JS custom misc. utilities
	└── vue/
		├── directives/               // Vue directives
		├── mixins/                   // Vue mixins
		└── plugins/                  // Vue plugins
	├── index.html.ejs                // Main HTML template
	├── main.js                       // Vue setup and main entry point for client app
	├── stylelint.config.js           // Linter configuration
	├── .htmllintrc                   // Linter configuration
	└── .eslintrc.js                  // Linter configuration
static/                              // Static files to host alongside product
test/
	└── e2e/                          // End-to-end tests on Nightwatch
		├── custom-assertions/
		└── specs/
	└── unit/                         // Unit tests on Karma and Mocha
		└── specs/
			├── components/
			├── models/
			├── services/
			└── store/
```



## Tooling

```
webpack/                             // Webpack build scripts
	└── env/                          // Environment configuration
test/
	└── e2e/
		├── nightwatch.conf.js        // End-to-end test runner configuration
		└── nightwatch.chrome.conf.js
	└── unit/
		└── karma.conf.js             // Unit test runner configuration
package.json                         // Dev and app dependencies, development scripts
.nvmrc                               // Node.js version
```

## Extras

```
.vscode/                             // Workspace settings for Visual Studio Code
```
