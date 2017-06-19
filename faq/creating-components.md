
# Creating a new component

**How do I create a new component?**

```
src/
	└── components/
		├── NewComponent.vue/
		├── OldComponent.vue/
		└── index.js
```

## 1. Create a new `.vue` file

`src/components/NewComponent.vue`

```html
<script>
	export default {
		name: 'new-component'
	}
</script>
<template>
	<div class="view-new-component">Foo</div>
</template>
<style lang="scss">
	.view-new-component {}
</style>
```

## 2. Add new component to manifest

`src/components/index.js`

```js
import NewComponent from './NewComponent';
export {
	...
	NewComponent
	...
};
export default {
	...
	NewComponent
	...
};
```

## 3. Use in parent component

`src/components/OldComponent.vue`

```html
<template>
	<div class="view-old-component">
		<new-component></new-component>
	</div>
</template>
```

## 4. Add tests

`test/unit/specs/components/NewComponent.spec.js`

```js
import Vue from 'vue';
import NewComponent from '@vue-components/NewComponent';

describe('NewComponent.vue', function () {
	it('should do something', function () {

		// Set up a new instance of the component
		const Constructor = Vue.extend(NewComponent);
		const vm = new Constructor().$mount();

		// Expected results
		expect(vm.$el.querySelector('h1').textContent)
			.to.equal('Hello world!');

	});
});
```
