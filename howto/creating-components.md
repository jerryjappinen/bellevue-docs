
# Creating a new component

```
src/
  |__ vue-components/
    |__ NewComponent.vue/
    |__ OldComponent.vue/
```

## 1. Create a new `.vue` file under `src/vue-components`

`src/vue-components/NewComponent.js`

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

## 2. Use in parent component

`src/vue-components/OldComponent.js`

```html
<script>
	import NewComponent from '@components/NewComponent'

	export default {
		name: 'old-component',

		components: {
			NewComponent: NewComponent
		}

	}
</script>
<template>
	<div class="view-old-component">
		<new-component></new-component>
	</div>
</template>
```

## 3. Add tests

...
