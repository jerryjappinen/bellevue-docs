
# Services

```
src/
	|_ services/
		|_ someService.js
```

[See included examples on GitHub](https://github.com/Eiskis/bellevue/tree/master/src/services)

Services are viewless, "global" Vue objects that can be shared across components. They can expose values, computed values and helpers like any other Vue object. Change detection is enabled, and you can use any data, computed values and methods of a service in your components or other parts of the application code as you would expect.

Services are used for things such as storing and providing access to state of shared UI elements (like "is a popup visible?") and other UI-related things (like "what is the current time?").

## Services vs. Vuex

Services can be used for most tasks that a full-blown Vuex state management might be used. Both expose a shared state to multiple components fairly efforlessly.

Services in this template are written as Vue objects just like [models](models.md) and [components](components.md). Vuex uses a different pattern, meaning the codebase is split into more diverse set of patterns than if using only services.

Currently the `$data` of a service object is not stored in local storage like with Vuex, so when the user reloads the page, the state of these services will be the defaults. Loading values from persistent storage and initialisint a service with them can be done fairly easily however.

Note that this template ships with **both** Vuex and services, and you can choose to build your app on either or both.
