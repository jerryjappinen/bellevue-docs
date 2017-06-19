
# Stack summary

- Fully running on Node
	- Version configured in `.nvmrc`
	- Dependencies are imported from npm and are configured in `package.json`
- Webpack + Babel
	- ES6 with imports, exports etc.
	- Modern frontend tooling built on auto loaders
	- Infinitely configurable and extendable
	- Highly customized per environment
- Supports for three distinct environments:
	- `dev`
	- `prod`
	- `test`
- Command line
	- Linters, build and other scripts are also available on CLI
	- Configured in `package.json`
- Vue
	- Modern, fast reactive UI framework
	- View components and generic Vue objects supported
	- Plugins and directives can be added
	- Global state management on Vuex
- Styles
	- SCSS
	- PostCSS
	- Autoprefixer
	- Tooling for both global style builds and component styles in `.vue` files
	- CSS modules and `scoped` component styles available but currently not used
	- Vendor styles can be included but currently not used
- Tests
	- Unit tests on Karma
	- End-to-end tests on Nightwatch

## Build scripts

You can find environment-specific build scripts under `webpack/`. To add more automation or support for new languages in the pipeline, you can include Webpack plugins and loaders in these files.

You should generally **not** have to touch these files during application development, as there is utility code included that reads values from [centralised configuration](../app/configuration.md) from simpler configuration files.

## Webpack plugins

- [`favicons-webpack-plugin`](https://github.com/jantimon/favicons-webpack-plugin) generates app icons for multiple platforms from one source file

## Webpack loaders

- [`vue-loader`](http://vue-loader.vuejs.org/en/) loads `.vue` files
- [`sass-loader`](https://github.com/webpack-contrib/sass-loader) loads `.scss` files
- [`postcss-loader`](https://github.com/postcss/postcss-loader) loads CSS files
- [`external-svg-sprite-loader`](https://www.npmjs.com/package/external-svg-sprite-loader) loads SVGs and compiles them into sprites
