
# Using a new Vue plugin

**How do I install a new Vue plugin?**

```
src/
	|_ components/
		|_ MyVomponent.vue
	|_ vue/
		|_ plugins/
			|_ vue-plugin-foo.js/
	main.js
```

## 1. Add your plugin as dependency

```bash
npm install vue-plugin-foo --save
```

## 2. Add a new plugin setup file

`src/vue/plugins/vue-plugin-foo.js`
``

```js
import Vue from 'vue';
import VuePluginFoo from 'vue-plugin-foo';

// Get your app configuration from `src/config/`
import config from '@config';

Vue.use(VuePluginFoo, {
	fooOptionName: config.fooOptions.fooOptionName
});
```

## 3. Import plugin setup in main.js

`src/main.js`

```js
import '@plugins/vue-plugin-foo';
```

## 4. Use plugin as intended in components

`src/components/MyVomponent.vue

```js
computed: {
	someProperty: function () {
		return this.$plugin.somePluginProperty;
	}
}
```
