
# Using a new Vue plugin

**How do I install a new Vue plugin?**

```
src/
	├── components/
	.	└── MyComponent.vue
	└── vendor/           // Setup files for all vendor libraries
		├── vue-foo.js    // Vue plugin's setup
		└── vue.js        // Main Vue instance setup
```

## 1. Add your plugin as dependency

```bash
npm install vue-foo --save
```

## 2. Add a new plugin setup file

`src/vendor/vue-foo.js`
``

```js
import Vue from 'vue';
import VueFoo from 'vue-foo';

// Get your app configuration from `src/config/`
import config from '@config';

Vue.use(VueFoo, {
	fooOption: config.meta.title
});

export default VueFoo
```

## 3. Import plugin setup in the main Vue setup file

**3.1** If plugin does not require injecting to main Vue instance (e.g. `vue-meta`):

`src/vendor/vue.js`

```js
import './vue-foo';
import './vue-meta';
// ...
```

**3.2** If plugin requires injecting to main Vue instance (e.g. `vue-router`):

`src/vendor/vue.js`

```js
import foo from './vue-foo';
import router from './vue-router';

// ...

const options = {
	el: '#app',
	foo, // <- add this (see plugin docs for details)
	router,
	template: '<app></app>'
}
```

## 5. Use plugin as intended in components

`src/components/MyComponent.vue`

```js
computed: {
	someProperty: function () {
		return this.$foo.fooProp;
	}
}
```
