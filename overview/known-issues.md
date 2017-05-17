
# Known issues

## Pipeline

- Desired source code order is hard to set
	- Utility styles should come after component styles, but style source order is magical
	- Not currently an issue with JS
- The app icon generator webpack plugin
	- Does not support passing all options to the plugin generating meta tags with color information etc.
	- Does not compile a web favicon
	- https://github.com/jantimon/favicons-webpack-plugin
- Dev server and unit test startup time has increased dramatically
	- Who's the culprit?
	- With app icon builds: startup around 30 s
	- Without: still around 10 s
	- Compiling all SCSS is probably slow as well
	- Recompiling after saving changes to a file generally around 750-1500 ms

## Client-side features

- `vue-meta`
	1. Has issues with `keep-alive`
	2. Parent component title will flicker when changing pages

## Development and IDE support

- The Stylelint extension for Visual Studio Code only lints `.css` and `.scss` files
	- Linting via command line or webpack still works as expected even in `.vue` and `.html` files
