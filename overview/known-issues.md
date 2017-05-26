
# Known issues

## Pipeline

- Desired source code order is hard to set
	- Utility styles should come after component styles, but style source order is magical
	- Not currently an issue with JS
- The app icon generator Webpack plugin
	- Does not support passing all options to the plugin generating meta tags with color information etc.
	- Does not compile a web favicon
	- https://github.com/jantimon/favicons-webpack-plugin
- Dev server and unit test startup time has increased dramatically
	- Who's the culprit?
	- With app icon builds: startup around 30 s
	- Without: still around 10 s
	- Compiling all SCSS is probably slow as well
	- Recompiling after saving changes to a file generally around 750-1500 ms

## Testing

Testing is a pain to set up. JS test runners and frameworks require a lot of delicate low-level setup work. Components that need to be mounted, update queues that need to be processed and asynchronous logic will also make testing more complicated.

Currently some tests pass, some don't, without very clear indication as to why. The current test setup is almost untouched from what the original Vue template provides. It still has problems when making assertions about computed properties of Vue objects.

## Client-side features

- `vue-meta`
	1. Has issues with `keep-alive`
	2. Parent component title will flicker when changing pages

## Development and IDE support

- `.ejs` files are not currently linted. We only have one such file and it very rarely changes though.
- Visual Studio Code does not seem to support intellisense for JavaScript embedded in HTML, and by extension `.vue` files.
	- Seriously what?
- The Stylelint extension for Visual Studio Code only lints `.css` and `.scss` files
	- Linting via command line or Webpack still works as expected even in `.vue` and `.html` files
