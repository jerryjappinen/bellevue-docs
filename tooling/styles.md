
# Styles processing

This template comes preconfigured with support for both _preprocessing_ and _postprocessing_ in both _global styles_ and _component styles_.

## SCSS

`@imports` work as expected in `.scss` code, including `.scss` aliases. Each `.scss` and `.vue` file explicitly define the `@imports` they need and can thus be built independently without errors.

Testing is not included for SCSS but is possible to include. This might make sense for ensuring the complex utility class generation works as intended.

## PostCSS

PostCSS will autoprefix all styles according to the browser support defined in the `browserslist` property of `package.json`.
