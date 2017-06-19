
# Services

```
src/
	|_ services/
		|_ someService.js
```

[See included examples on GitHub](https://github.com/Eiskis/bellevue/tree/master/src/services)

Services are viewless, "global" Vue objects that can be shared across components. They can expose values, computed values and helpers like any other Vue object. Change detection is enabled, and you can use any data, computed values and methods of a service in your components or other parts of the application code as you would expect.

Services are used for things such as storing and providing access to shared UI state (for example, track if a popup is visible) or other things that are not directly related to any specific UI elements (for example, tracking the current time). The reason you might use a service over [utilities](../app/utilities.md) for these things is that change detection is enabled when the shared state changes.

## Services vs. Vuex

Services can be used for most tasks that a full-blown [Vuex](../app/vuex.md) state management might be used. Both expose a shared state to multiple components fairly efforlessly.

Services in this template are written as Vue objects just like [models](models.md) and [components](components.md). Vuex uses a different pattern, meaning the codebase is split into more diverse set of patterns than if using only services.

Note that this template ships with **both** Vuex and services, and you can choose to build your app on neither, either or both.
