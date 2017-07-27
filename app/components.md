
# View components

```
src/
	└── components/
		└── MyComponent.vue
```

[See included components on GitHub](https://github.com/Eiskis/bellevue/tree/master/src/components)

Components are **reusable** and **nestable** UI snippets that encapsulate view logic in one... component. In Vue, a component is authored as one HTML-like file with three elements: `template`, `script` and `style`. Vue's view components closely follow web standards and are built on HTML, JS and CSS respectively.

- Official guide: [vuejs.org/v2/guide/components](https://vuejs.org/v2/guide/components)
- Full reference: [vuejs.org/v2/api](https://vuejs.org/v2/api/)

![Vue component lifecycle](https://vuejs.org/images/lifecycle.png)

## Best practices

- Keep components small. If a component bloats, split it. It's better to have many small components than small number of bloated ones.
- Create dedicated components for **pages** which users navigate to and which have routes associated with them.
	- These page components should not do a lot more than define meta information and include other components and `<route-views>`.
	- Page can be wrapped in shared components such as `<page>`, which is preconfigured
- In `.vue` files, write the code in the following order:
	- `<script>`
		- vendor imports
		- helpers
		- view model (`export default { ... }`)
	- `<template>`
	- `<style>`

### View model

- View models are only for declaring the behavior, styling and structure of one component as clearly as possible.
- View models should **not** include any business logic code.
	- Feel free to `import` [models](models.md) and vendor libraries as needed.
- Recurring view model code can be reused:
	- You can write custom plugins and directives for Vue.
	- Plugins and directives are also not for business logic though.

### Templating

- Always have one parent element in your component.
- Always use the `:` and `@` shorthands with bindings.
- Avoid adding a lot of JS expressions in the template. Add a computed property in the view model instead.

### Styles

You can and should use SCSS in component styles. You can `@import` the shared styles to use shared mixins and other tools.

One components can generally appear under multiple different parent components in the application. In order to make it easy to customize component styles in any given context, it's best to

- Give your component a parent class that matches the component, prefixed with `.view-`.
- Name other elements with component-specific class names matching the component nime.
- Provide prefixed state classes such as `.view-my-component-enabled` and `.view-my-component-disabled`
- Avoid unnecessary nesting these prefixed classes, because this increases specificity and makes them harder to customize per context.
- Generic classes such as `.is-active` should be nested under the prefixed ones however.
- If you're writing a lot of code targeting elements by tag name, it's probably better to add a class name.

## External dependencies

You can import externally authored components anywhere you need them:

```html
<script>
	import VueSliderComponent from 'vue-slider-component';

	export default {
		name: 'my-component',

		components: {
			VueSliderComponent
		},

		...
	}
</script>

<template>
	<div class="view-my-component">
		<vue-slider-component></vue-slider-component>
	</div>
</template>
```

## Component blueprint

```html
<script>
	export default {
		name: 'my-component',

		data: function () {
			return {};
		},

		props: {},

		computed: {},

		methods: {},

		// https://vuejs.org/v2/api/#Options-Lifecycle-Hooks
		beforeCreate: function () {},
		created: function () {},
		beforeMount: function () {},
		mounted: function () {},
		beforeUpdate: function () {},
		updated: function () {},
		activated: function () {},
		deactivated: function () {},
		beforeDestroy: function () {},
		destroyed: function () {}

	}
</script>

<template>
	<div class="view-my-component">
		<div class="view-my-component-something">
			<spinner></spinner>
		</div>
	</div>
</template>

<style lang="scss">
	@import '~@shared-styles';

	.view-my-component {}

	.view-my-component-something {
		&.is-active {}
	}

</style>
```

## Sample code

```html
<script>

	// Vendor code
	import _ from 'lodash';

	// Component's view model
	export default {

		name: 'my-component',

		data: function () {
			return {
				someParameter: false,
				color: 'red',
			};
		},

		props: {
			someInputParameter: {
				type: String,
				required: false,
				default: 'Foo'
			}
		},

		computed: {

			titleToRender: function () {

				if (this.someParameter) {
					return 'Some special title';

				} else if (this.someInputParameter) {
					return _.trim(this.someInputParameter);
				}

				return 'Default title';
			}

		},

		methods: {

			setSomeParameter: function () {
				this.someParameter = true;
			}

			changeColor: function () {
				this.color = (this.color === 'red') ? 'green' : 'red';
			}

		},

		created: function () {
			setTimeout(this.setSomeParameter, 4 * 1000);
		},

		beforeDestroy: function () {
			console.log('beforeDestroy');
		}

	};

</script>

<template>

	<div class="view-my-component">

		<!-- HTML element with dynamic bindings -->
		<h1 :data-title="titleToRender"
			@click="changeColor"
			ref="titleElement">
			{{ titleToRender }} <em :style="{ color: color }">Color!</em>
		</h1>

		<!-- Child component -->
		<spinner></spinner>
	</div>

</template>

<style lang="scss">
	@import '~@shared-styles';

	.view-my-component {
		color: blue;
	}

</style>
```
