
# Extending Vue

## Vue objects

Anything can be written as a Vue object. You can always create a new Vue instance with `new Vue({ ... })` (this is how our [services](services.md) are written) and write an object that can take advantage of Vue's change detection, computed properties, lifecycle hooks and other goodies. Vue can deliver a lot of great functionality even if you never intend to render anything.

```js
// somefile.js
var someService = new Vue({
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
export default someService;

// anotherfile.js
import s from 'somefile.js';
console.log(s.someNumber, s.someNumberTimesTen); // 1, 10
s.iterate();
console.log(s.someNumber, s.someNumberTimesTen); // 2, 20
```

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

## Vue mixins

- [Official guide on Vue mixins](https://vuejs.org/v2/guide/mixins)

## Vue directives

- [Official guide on Vue directives](https://vuejs.org/v2/guide/custom-directive)

## Vue plugins

What exactly is a "Vue plugin" is not strictly defined. Generally plugins are externally managed JS packages that add functionality as parameters, methods, directives and/or mixins to Vue either globally or on component level.

Vue provides a way to install and use a plugin, but other than that it's up to the author to use the API of Vue to deliver the intended functionality in whatever format they wish. Because of this, it can take some time to learn the best practices about authoring Vue plugins, especially if you expect change detection to work reliably. Because of this, it's better to write custom code as [custom utilities](services.md) or [custom services](services.md).

- [Official guide on Vue plugins](https://vuejs.org/v2/guide/plugins)
