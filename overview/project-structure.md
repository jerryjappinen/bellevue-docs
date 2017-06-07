
# Project structure



## App source

```
docs/                                // Documentation generated from codebase
src/
	|_ app-icon/                     // App icon assets
	|_ assets/                       // Generic asset files such as images
	|_ components/                   // Views, single-file .vue components
	|_ config/                       // Custom pipeline and client-side configuration
		|_ config-aliases.js
		|_ config-base.js
		|_ config-routes.js
	|_ fonts/                        // Web font files
	|_ models/                       // JS business logic objects
	|_ services/                     // JS custom (reactive) services
	|_ store/                        // JS state management code
	|_ styles/                       // Global base styling and style utilities
		|_ base/
		|_ definitions/
		|_ keyframes/
		|_ mixins/
		|_ normalize/
		|_ plugin-overrides/
		|_ toolchain/
		|_ transitions/
		|_ utilities-base/
		|_ utilities-composed/
	|_ svg/                          // SVG assets that will be compiled into a sprite
	|_ util/                         // JS custom misc. utilities
	|_ vue/
		|_ directives/               // Vue directives
		|_ mixins/                   // Vue mixins
		|_ plugins/                  // Vue plugins
index.html.ejs                       // Main HTML template

// Linter configuration
.eslintrc.js
.htmllintrc
stylelint.config.js

// Static files to host alongside the production build
static/

// End-to-end and unit tests
test/
  |_ e2e/
    |_ custom-assertions/
  |_ unit/
    |_ specs/
      |_ components/
      |_ models/
      |_ store/

```



## Pipeline

```
build/         // Webpack build scripts
config/        // Webpack environment configuration
.nvmrc         // Node.js version
package.json   // Dev and app dependencies, development scripts
```

## Extras

```
.vscode/
```
