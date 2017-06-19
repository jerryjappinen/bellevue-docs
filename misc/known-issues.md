
# Known issues

Concrete issues are [tracked on GitHub](https://github.com/Eiskis/bellevue/issues). This page has some additional commentary on some potential issues and gotchas.

## Tooling

- Source code order is sometimes hard to control
	- Source code order matters in JS and in CSS
	- Minor issue (matter of opinion): utility styles should come after component styles, but injection order is magical
	- Not currently an issue with JS or other parts of the code
	- Could perhaps be controlled manually by opting out of auto inject, or using `require()` instead of `import` for some SCSS files
- Dev server and unit test startup time increases dramatically when functionality is added
	- App icon compilation is the biggest culprit (startup around 30 sec)
	- Complex SCSS pipeline after that (startup around 10 sec without app icons)
	- Recompiling after saving changes to a file generally around 750-1500 ms
	- Webpack is pretty good at only compiling what it needs during development, mostly it's just the startup time that is affected
- App icon generator Webpack plugin
	- Prints extraneous meta tags such as theme color
	- https://github.com/jantimon/favicons-webpack-plugin

## Unit testing

Currently some tests pass, some don't, without very clear indication as to why. The current test setup is almost untouched from what the original Vue template provides. It still has problems when making assertions about computed properties of Vue objects.

## Client-side features

- Very minor issues with `vue-meta`
	- Does not work reliably with `keep-alive`
	- Parent component title will flicker when changing pages
		- Not a problem if title is controlled by `App.vue` instead of page components, which is probably better anyway

## Development and IDE support

- `htmllint` is not integrated with Webpack 2 yet
- VS Code: `.vue` files
	- VS Code does not seem to support intellisense for JS that is embedded HTML, like in `.vue` files
	- The Vetur extension provides a lot of functionality however
- VS Code: Stylelint only works for `.css` and `.scss` files, not `.vue` files
	- Linting via command line or Webpack still works as expected even in `.vue` and `.html` files
