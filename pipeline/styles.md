
# Styles processing

This stack is configured to support both A) SCSS preprocessing and B) PostCSS postprocessing in both 1) global styles and 2) component styles.

PostCSS currently does only autoprefixing according to the browser support defined in `package.json`.

`@imports` work as expected in `.scss` code, including `.scss` aliases. Each `.scss` and `.vue` file explicitly define the `@imports` they need and can thus be built independently without errors.

Testing is not included for SCSS but is possible to include. This might make sense for ensuring the complex utility class generation works as intended.
