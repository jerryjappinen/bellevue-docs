# Stylesheet architecture

Any practical modern web application will be built with a mix of **global** and **component-specific** styling. CSS's cascade makes this easy, so long as you keep things organised and use a sensible naming convention. Bellevue offers a full-featured, preconfigured architecture for architecturing (S)CSS code in a scalable way.

## Global styles structure

```
└── src/
	└── styles/
		├── defaults/          // BAse styling for <body> and other elements
		├── functions/         // Sass functions
		├── keyframes/         // CSS animation definitions
		├── mixins/            // Sass mixins
		├── transitions/       // Named transition definitions
		├── utilities/         // CSS utility classes
		|
		├── constants.scss     // Global Sass variables and defaults
		├── font-face.scss     // Generates @font-face rules for local web fonts
		├── functions.scss     // All Sass functions
		├── mixins.scss        // All Sass mixins
		├── normalize.scss     // Global resets
		|
		└── global.scss        // All global base styling
```

All global CSS is output by importing `global.scss` in  `App.vue`. All mixins, functions and global variables are imported by `mixins.scss` and `functions.scss` respectively, and then .

In your final output, global stylesheets component styles come after global styles.

## Component styles

Components are written as `.vue` files, which include a `<style>` tag for writing component styles. All functions, mixins and global variables are injected into your components automatically.

Vue's `<style scoped>` is not used by default, as this will make it difficult to override child component styles in a parent component. If you've traditionally had troubles with the cascade though, and are not interested in overwriting child component styles per context, you might want to use `scoped` in your components, and only allow customizing the component via props.

## Sass variables in JS

Commonly accessed style variables in Sass are set in `constants.scss`. You can access these in JS by importing [`@config/styles`](../app/config.md).
