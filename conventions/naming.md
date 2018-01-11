# Naming conventions

## kebab-case

Sass files:

```
src/
	└── styles/
		└── shared.scss
```

Sass variable names and mixins:

```scss
$some-breakpoint: 800px;

@mixin viewport-over ($breakpoint) {
	@media (min-width: ($breakpoint)) {
		@content;
	}
}
```

CSS classes and HTML tags and attributes:

```scss
.c-my-component {}
```

```html
<div class="c-my-component" data-some-attr="Some value"></div>
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

export const actions = {
	doSomething: function (context) {
		context.commit('ITERATE_VALUE');
	}
};
```

## CapitalCamelCase

Component names and files:

```
src/
	└── components/
		└── MyComponent.vue
	└── svg/
		└── MyVectorAsset.svg
```

Models, constructor classes and component names in JS.

```js
import SomeModel from '@models';
var modelInstance = new SomeModel();
modelInstance.doSomething()
```

## camelCase

- `camelCase` for all other `vuex` keys (state variables, getters, actions ...)
- camelCase for all other exported values in JS
- camelCase for all other JS files and variables
