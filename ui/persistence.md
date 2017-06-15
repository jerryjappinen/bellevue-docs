
# Persistence

## Persistence in components

[Components](./app/components.md) can easily store their state in Local Storage. This is implemented with a global mixin, which tracks a computed parameter `persist` and stores it whenever it changes. When the component

In order for peristence to work, we need to have a key to store the persistent values with. To make sure each component has one, you **must** define either the component's `name` property (which is a good practice) or a _computed_ property `persistKey` for your component in order for peristence to work.

Any two Vue objects with the same `persistKey` (which defaults to the object's `name`) will **share the same persistent values**. This means that by default, persistence is shared across all instances of the same component. When authoring your code, be aware of this so that persistence works as expected for your users.

```js
	// MyPersistentComponent.vue
	// ...
	name: 'foo-component',
	data: function () {
		return {
			someValue: 'Foo'
		};
	},
	computed: {
		persist: {

			// The mixin adds a watcer for this
			// Whenever this value changes, it is stored in local storage
			get: function () {
				return {
					someValue: 'Foo'
				};
			},

			// Called when data is loaded
			// This is where you define how you treat the stored data
			// This could be more complicated, for example you could decide to load the values only with current route
			set: function (stored) {
				if (stored.someValue) {
					this.someValue = stored.someValue;
				}
			}

		}
	}
	// ...
```

If you are in a situation where you want to persist data per instance, you should probably store that data elsewhere (Vuex or services).

[See source for global mixin](https://github.com/Eiskis/vue-webpack/tree/master/src/vue/mixins/persist.js)

## Persistence in services

[Services](./app/services.md) can also store their state. It works the same way as with components, i.e. through the `persist` computed value. This is handled by the root Vue instance, which inherits the mixin functionality and stores/loads the state of each service (this is because global mixins are not injected to services).

See example: [Panels service](https://github.com/Eiskis/vue-webpack/tree/master/src/services/panels.js)

**Note:** as services do not have access to the root Vue instance, they cannot check for things such as `this.$route` when setting persistent values from local storage.

## Persistence in Vuex

Persistence in Vuex is not currently implemented, but is easy to add with plugins.

[See Vuex plugins on Awesome Vue](https://github.com/vuejs/awesome-vue#vuex-utilities)
