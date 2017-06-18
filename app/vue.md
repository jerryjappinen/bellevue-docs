
# Extending Vue

This project template provides a framework for writing different parts of your app in a structured way powered by Vue:

- [Components](components.md)
- [Models](models.md)
- [Services](services.md)
- [Utilities](utilities.md) (plain JS, not Vue)

The following topics will teach you mode about how and why these different building blocks work, and how to extend Vue for more advanced use cases.

## Vue mixins

[Official guide on Vue mixins](https://vuejs.org/v2/guide/mixins)

Vue mixins can be added under `src/vue/mixins/`. Global mixins defined there will be registered automatically and will extend your components.

## Vue directives

[Official guide on Vue directives](https://vuejs.org/v2/guide/custom-directive)

Vue mixins can be added under `src/vue/directives/`. Global mixins defined there will be registered automatically and will be available in your components.

## Vue plugins

[Official guide on Vue plugins](https://vuejs.org/v2/guide/plugins)

Vue plugins can be added under `src/vue/plugins/`.

There's no strict definition for what exactly is a "Vue plugin". Generally plugins are externally managed JS packages that add functionality as parameters, methods, directives and/or mixins to Vue either globally or on component level.

[Guide to installing new plugin](../faq/vue-plugins.md)

### Writing custom plugins

Vue provides a way to install and use a plugin, but there is no strict and guided plugin architecture. It's up to the author to use the API of Vue to deliver the intended functionality in whatever format they wish. Because of this, it can take some time to learn the best practices about authoring Vue plugins, especially if you expect change detection to work reliably. Keep this in mind if you want to publish custom plugins.

## Initializing new Vue objects

Anything can be written as a Vue object. You can always create a new Vue instance with `new Vue({ ... })` (this is how our [services](services.md) are written) and write an object that can take advantage of Vue's change detection, computed properties, lifecycle hooks and other goodies. Vue can deliver a lot of great functionality even if you never intend to render anything.

```js
// somefile.js
export default new Vue({
	data: function () {
		return {
			someNumber: 1
		};
	},
	computed: {
		someNumberTimesTen: function () {
			return this.someNumber * 10;
		}
	},
	methods: {
		iterate: function () {
			this.someNumber++;
		}
	}
});
```

```js
// anotherfile.js
import thing from 'somefile.js';
console.log(thing.someNumber, thing.someNumberTimesTen); // 1, 10
thing.iterate();
console.log(thing.someNumber, thing.someNumberTimesTen); // 2, 20
```

## Extending new Vue objects

You can also use `Vue.extend({ ... })` to write new models that you can instantiate later (this is how our [models](models.md) are written).

```js
// somefile.js
var Foo = Vue.extend({
	props: {
		title: {
			type: String,
			default: 'Foo'
		}
	},
	computed: {
		titleWithPrefix: function () {
			return 'Bar ' + this.title;
		}
	}
});
export default Foo;
```

```js
// anotherfile.js
import Foo from 'somefile.js';

// Create new object
// titleWithPrefix will be 'Bar Bar'
var f = new Foo({
	propsData: {
		title: 'Bar'
	}
});

// titleWithPrefix will be 'Bar Vue'
f.title = 'Vue';
```

## Injecting any library into components

If you prefer to write component code with plugins available in `this` (such as `this.$http`), you can inject any library into the Vue prototype as explained by the Vue team [on Medium](https://medium.com/the-vue-point/retiring-vue-resource-871a82880af4).

For example, to inject [Axios](../ui/http.md) into Vue instead of using it like any other vendor code, you can load it up like other plugins like this:

```js
// src/vue/plugins/vue-http.js
import Vue from 'vue';
import Axios from 'axios';
Vue.prototype.$http = Axios;
export default Axios;
```

```js
// src/vue/plugins/index.js
import VueHttp from './vue-http';
export {
	VueHttp,
	...
};
export default {
	VueHttp,
	...
};
```

After this, Axios is available as `this.$http` in your components.
