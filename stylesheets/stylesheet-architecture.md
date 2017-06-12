
# Stylesheet architecture

Any practical modern web application will be built with a mix of stylesheet code, both global stylesheet code and component-specific style code.

`Eiskis/vue-webpack` offers a full-featured, preconfigured architecture for architecturing (S)CSS code in a scalable way. This architecture is easy to streamline if you feel your project needs this, but it's probably better to leave it in place as it's still fairly easy to navigate.

## Global styles

```
|_ src/
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
		|_ global.scss               // All global base styling
		|_ shared.scss               // All SCSS constants and mixins
		|_ utilities.scss            // All global CSS utilities
```

`global.scss` and `utilities.scss` are imported by `App.vue`.

**Known issue:** it is difficult to control the exact order that stylesheets are injected into `index.html` in Webpack. `utilities.scss` are _currently injected before_ component styles, but they _should be injected after_ component styles to be more effective and reduce the need for overqualified selectors.

## Component styles

Components are written as `.vue` files, which include a `<style>` tag for writing component styles.

Vue's `<style scoped>` is **not** used, as this will break the cascade. If you've traditionally had troubles with the cascade though, and are not interested using the power of overwriting child component styles per context for good, you might want to use `scoped` in your components.

## Sharing SCSS tools

In both global and component styles, you can import any SCSS mixins and constants you need. The easiest way to do this is to simply import the shared styles like this:

```scss
@import '~@styles/shared';
```

Notice that this does not result in any new CSS output. `shared.scss` only imports mixins and constants.
