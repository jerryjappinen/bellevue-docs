
# To do

- [ ] Persistent global state
	- Just store in localstorage or something
	- What about Vuex modules?
	- https://github.com/vuejs/awesome-vue#persistence
- [ ] Integrate `vue-resource`
- [ ] Integrate client-side form validation
	- https://github.com/vuejs/awesome-vue#validation
- [ ] Integrate localisation
	- https://github.com/vuejs/awesome-vue#i18n
- [ ] Services/plugins/global state modules
	- Feature detection (Wrap Modernizr?)
	- Some kind of date/time service with current time
	- Some kind of viewport service with screen size information (should emit throttled events perhaps?)
		- `this.$viewport.onChangeUnder(1400, function () { ... });`???
- [ ] More full-featured index.html templating
	- Add more full-featured meta tags
	- https://github.com/jantimon/favicons-webpack-plugin
	- https://github.com/jantimon/html-webpack-plugin#third-party-addons
- [ ] Example component with all supported functionality
	- `$watch`ing
	- All component lifecycle hooks
	- Using plugins from `this`
- [ ] Event usage examples
	- `_.debounce`
	- Integrate `vue-throttle-event`
	- Component event bindings (`this.$on`, `this.$emit`)
	- Keyboard/other event binding (will `this.$on('blur')` work out of the box for example?)
- [ ] Clean up pipeline
	- Move webpack scripting and other pipeline-related delicate configuration to non-confusingly named subfolders
	- Move important configs to `project.config.js`
- [ ] Formatted comments and intellisense for custom code

