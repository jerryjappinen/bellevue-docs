
# Styles processing

This template comes preconfigured with support for both _preprocessing_ and _postprocessing_ in both _global styles_ and _component styles_.

## Sass

`@imports` work as expected in `.scss` code, including `.scss` aliases. Each `.scss` and `.vue` file explicitly define the `@imports` they need and can thus be built independently without errors.

Shared functions, variables and mixins are injected into `.vue` components automatically, so you don't have to import them in every file.

Testing is not included for Sass but is possible to include. This might make sense for ensuring the complex utility class generation works as intended.

## PostCSS

PostCSS will autoprefix all styles according to the browser support defined in the `browserslist` property of `package.json`.
