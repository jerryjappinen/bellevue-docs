
# Naming conventions

## kebab-case

SCSS files:

```
src/
  |_ styles/
    |_ shared.scss
```

SCSS mixins:

```scss
@mixin viewport-over-large {
	@content
}
```

CSS classes and HTML tags and attributes:

```scss
.view-my-component {}
```

```html
<div class="view-my-component" data-some-attr="Some value"></div>
```

By extension, declared component names:

```js
export default {
	name: 'my-component'
	...
}
```

## UPPER_CASE_WITH_UNDERSCORE

`vuex` mutations

```js
export const mutations = {
	'ITERATE_VALUE': function (state) {
		state.someValue==;
	}
};
```

## camelCase

- `camelCase` for all other `vuex` keys
- camelCase for all other exported values in JS
- camelCase for all other JS files and variables

## CapitalCamelCase

Component names and files:

```
src/
|_ vue-components/
|_ MyComponent.vue
```

Models, constructor classes and component names in JS.

```js
import SomeModel from '@models';
var modelInstance = new SomeModel();
modelInstance.doSomething()
```

