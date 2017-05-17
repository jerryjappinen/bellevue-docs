
# Creating a new component

- Official guide: [vuejs.org/v2/guide/components](https://vuejs.org/v2/guide/components)
- Full reference: [vuejs.org/v2/api](https://vuejs.org/v2/api/)

Components are **reusable** and **nestable** UI snippets that encapsulate view logic in one... component. In Vue, a component is authored as one HTML-like file with three elements: `template`, `script` and `style`. Vue's view components closely follow web standards and are built on HTML, JS and CSS respectively.

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
