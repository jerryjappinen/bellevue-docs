
# Using a new Vue plugin

**How do I install a new Vue plugin?**

```
src/
	├── components/
	.	└── MyVomponent.vue
	└── plugins/
	.	└── vue-plugin-foo.js/
	└── vendor/
		└── vue.js/                // Main Vue instance setup
```

## 1. Add your plugin as dependency

```bash
npm install vue-plugin-foo --save
```

## 2. Add a new plugin setup file

`src/plugins/vue-plugin-foo.js`
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

## 3. Import plugin setup in the main Vue setup file

`src/vendor/vue.js`

```js
import '@plugins/vue-plugin-foo';
```

## 4. Use plugin as intended in components

`src/components/MyVomponent.vue`

```js
computed: {
	someProperty: function () {
		return this.$plugin.somePluginProperty;
	}
}
```
