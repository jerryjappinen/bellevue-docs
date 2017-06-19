
# Vuex

```
src/
	|_ store/
		|_ index.js
```

[See included example of single global store on GitHub](https://github.com/Eiskis/bellevue/tree/master/src/store)

Global state is for things that user can directly control and would expect (explicitly or implicitly) the application to know, keep track of and ensure persistence of (latter is currently not included). Global state is shared between components.

Official Vuex documentation is available at [vuex.vuejs.org](https://vuex.vuejs.org/en/).

## Alternatives

In Vuex, change detection is enabled, but the architecture used for writing global state code is different from writing other Vue code. Vuex can be powerful, but you might also consider using [services](services.md) if you're not sure you need it - they are shared Vue objects with global state, written as Vue objects instead of using the Vuex pattern.

Vuex is very complex, but well integrated into Vue development tools, and uses some common patterns shared with other state management solutions.

There are [many authored alternatives](https://github.com/vuejs/awesome-vue#state-management) out there.

## Removing Vuex

If you don't need Vuex, it might be better to just get rid of the extra complexity. It's also fairly easy to add back in later if you need it in the future.

1. Remove the `vuex` dependency from `package.json`
2. Remove or comment the parts in `src/vue/plugins/index.js` where `Vuex` is imported and exported.
3. Remove or comment the part in `src/main.js` where `plugins.vuex` is passed to Vue.
4. Remove the alias `@store` from `src/config/config.aliases.js`.
5. Remove `src/vue/plugins/vuex.js`.
6. Remove Vuex code from under `src/store/`.
7. Remove Vuex tests from under `test/unit/specs/store/`.
8. Clean up sample code that uses Vuex
	- Anything that imports from `@store`
	- In `.vue` components: anything that accesses `this.$store`
