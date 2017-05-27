
# Creating a new component

```
src/
  |__ components/
    |__ NewComponent.vue/
    |__ OldComponent.vue/
    |__ index.js
```

## 1. Create a new `.vue` file

`src/components/NewComponent.vue`

```html
<script>
	export default {
		name: 'new-component',
	}
</script>
<template>
	<div class="view-new-component">Foo</div>
</template>
<style lang="scss">
	.view-new-component {}
</style>
```

## 2. Add to components manifest

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

## 3. Add tests

...
