
# SCSS coding conventions

Global base and utility styles are written under `src/styles/`. Component-specific styles are written in each `.vue` file.

The coding style of the application code is defined as closely as possible with Stylelint. The rules are configured and annotated in:

```
src/
  |_ stylelint.config.js
```

## TL;DR

- Use tabs
- Use semicolons
- Use single quotes

## Gotchas

### Duplicate code while @importing

SCSS is a preprocessor, and outputs CSS. When you use `@import` to define dependencies in `.scss` files, any CSS output from those files will be included in the output. If multiple source files @import the same file, any output from the imported file will be included twice in the final output. This makes sense from the file processing perspective but is usually not what we want.

To avoid any issues, we follow the best practices:

- Declare shared mixins and variables _only_ in files that produce _no output_. This way, they can be imported for use in any context without affecting the output.
- Only use _@import_ in the following cases
	- Importing shared mixins and variables for use in a `.scss` or `.vue` file.
	- In manifest files which import a collection of source files for output (like `global.scss` and `utilities.scss`).
	- Importing said manifest files in root component (`App.vue`) or main template (`index.html.ejs`).
