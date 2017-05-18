
# View components

```
src/
  |__ vue-components/
    |__ MyComponent.vue/
```

- Official guide: [vuejs.org/v2/guide/components](https://vuejs.org/v2/guide/components)
- Full reference: [vuejs.org/v2/api](https://vuejs.org/v2/api/)

Components are **reusable** and **nestable** UI snippets that encapsulate view logic in one... component. In Vue, a component is authored as one HTML-like file with three elements: `template`, `script` and `style`. Vue's view components closely follow web standards and are built on HTML, JS and CSS respectively.

![Vue component lifecycle](https://vuejs.org/images/lifecycle.png)

## Best practices

- Keep components small. If a component bloats, split it. It's better to have many small components than small number of bloated ones.
- Create dedicated components for pages which users navigate to. These page components should not do a lot more than define meta information and include other components and `<route-views>`.

### View model

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

You can and should use SASS in component styles. You can `@import` the shared styles to use shared mixins and other tools.

One components can generally appear under multiple different parent components in the application. In order to make it easy to customize component styles in any given context, it's best to

- Give your component a parent class that matches the component, prefixed with `.view-`.
- Name other elements with component-specific class names matching the component nime.
- Avoid nesting these specific classes under the parent, because this increases specificity and makes them harder to customize per context.
- Do nest generic state classes such as '.is-active'
- If you're writing a lot of code targeting elements by tag name, it's probably better to add a class name.

## Component blueprint

```html
<script>
	import Spinner from '@components/snippets/Spinner';
	import SomeDirective from '@directives/some-directive';
	export default {
		name: 'my-component',

		components: {
			Spinner: Spinner
		},

		directives: {
			SomeDirective: SomeDirective
		},

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
		<div class="view-my-component-something"></div>
	</div>
</template>

<style lang="scss">
	@import '~@styles/shared.scss';

	.view-my-view {}

	.view-my-view-something {
		&.is-active {}
	}

</style>
```

## Sample code

```html
<script>

	// Vendor code
	import _ from 'lodash';

	// Child components
	import Spinner from '@components/snippets/Spinner';

	// Directives used in this component
	import SomeDirective from '@directives/some-directive';

	// Component's view model
	export default {

		name: 'my-component',

		// Declare which other components are nested in this component
		components: {

			// NOTE: Spinner defines its own name (as 'spinner')
			Spinner: Spinner

		},

		// Declare which directives are used in this component
		directives: {
			SomeDirective: SomeDirective
		},

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
		<h1 :data-title="titleToRender" @click="changeColor" ref="titleElement">{{ titleToRender }} <em :style="{ color: color }">Color!</em></h1>
	</div>

</template>

<style lang="scss">
	@import '~@styles/shared.scss';

	.view-my-component {
		color: blue;
	}

</style>
```
