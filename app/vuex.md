# Vuex

Vuex is preconfigured and enabled by default.

```
src/
	└── store/
		├── myModule.js
		└── index.js
```

Vuex is a **state management pattern + library** for managing global state in Vue applications. Global state is shared between components, and can be further split into modules, persisted across sessions on local storage etc. You can also unit test your getters, mutations, and actions with Jest in isolation from your components.

- [Example of store](https://github.com/Eiskis/bellevue/tree/master/src/store)
- [Official Vuex documentation](https://vuex.vuejs.org/en/)
- [Example of Vuex unit test](https://github.com/Eiskis/bellevue/tree/master/unit/store/myModule.spec.js)

## Alternatives

The Vuex pattern is different from the other parts of your code, and can feel weird or unnecessarily complete. Vuex can be powerful, but you might also consider using [services](services.md) if you're not sure you need it. There are also [many authored alternatives](https://github.com/vuejs/awesome-vue#state-management) out there.

## Removing Vuex

If you don't need Vuex, it might be better to just get rid of the extra complexity. It's also fairly easy to add back in later if you need it in the future.

1. Remove or comment out the `vuex` import and injection in `src/vendor/vue.js`
2. Remove the Vuex card from `PageDemo.vue`

To completely clean up your codebase:

1. Remove `src/vendor/vuex.js`
2. Remove `src/store/`
3. Remove `unit/store/`
4. Remove the alias `@store` from `src/config/config.aliases.js`
