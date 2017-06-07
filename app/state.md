
# Global state management

- Official Vuex docs: [vuex.vuejs.org](https://vuex.vuejs.org/en/)

Global state is for things that user can directly control and would expect (explicitly or implicitly) the application to know, keep track of and ensure persistence of. Global state is shared between components.

In Vuex, change detection is enabled, but the architecture used for writing global state code is different from writing other Vue code. Vuex can be powerful, but you might also consider using [services](services.md) if you're not sure you need it.


## Alternatives

How complex should we make global state management?

Vuex is very complex, but well integrated into Vue development tools, and uses some common patterns shared with other state management solutions.

There are [many authored alternatives](https://github.com/vuejs/awesome-vue#state-management) out there. Simply writing custom services as viewless Vue objects can also work very nicely.
