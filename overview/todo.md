
# To do

## Pipeline

- [ ] Split global state management
	- Vuex also supports splitting modules
	- Actions, getters, etc. can also be split into different files easily
	- Is using multiple stores an antipattern?
	- What are the best practices for this? Need to look at a real application.
- [ ] Persistent global state
	- Just store in localstorage or something
	- What about Vuex modules?
	- https://github.com/vuejs/awesome-vue#persistence
- [ ] More full-featured index.html templating
	- Add more full-featured meta tags
	- https://github.com/jantimon/favicons-webpack-plugin
	- https://github.com/jantimon/html-webpack-plugin#third-party-addons
- [ ] Get tests to work as expected

## Application code

- [ ] Integrate localisation
	- https://github.com/vuejs/awesome-vue#i18n
- [ ] Integrate client-side form/input validation
	- https://github.com/vuejs/awesome-vue#validation
- [ ] Time formatting
	- Wrap `moment.js` in time service?
- [ ] Some kind of env/device service
	- Feature detection
	- Touch vs. no touch
	- Wrap Modernizr?
- [ ] Tests for models
- [ ] Tests for services
- [ ] Inject services into components?
- [ ] Try `vue-supply`, `vue-apollo` and GraphQL
	- https://github.com/Akryum/vue-supply

## Components

- [ ] Small checkmark element
- [ ] Text, email, password
- [ ] Number fields
- [ ] Date picker
- [ ] Reliable in-place popover positioning
- [ ] Click handling and blur events for closing in-place popover
- [ ] List with pagination
- [ ] Prevent double click text select in all controls
- [ ] Tabs

## Examples and docs

- [ ] Write about controls vs form elements
- [ ] Write about services
	- What they do
	- How they work
	- Reference to existing services
	- Write howto about writing a new one
- [ ] Explain the difference between util, services and state
	- Utils are custom libraries of common functions that could just as well be external libraries. They are only included as integrated libraries and not published separately for convenience and the fact that they are written for specific needs instead of providing a full-fledged experience as an external library to other developers. Changes are not automatically detected.
	- Services are viewless, "global" Vue objects that can have values, computed values and helpers. They are recomputed during startup and runtime. Change detection is enabled but persistence is not.
	- State is for things that user can directly control and would expect (explicitly or implicitly) the application to know, keep track of and ensure persistence of. Change detection is enabled, but writing code that mutates it has its own architecture.
- [ ] Event usage examples
	- `_.debounce`
	- Using `vue-throttle-event`
	- Component event bindings (`this.$on`, `this.$emit`)
	- Binding modifiers (`.stop`)
	- Keyboard/other event binding (will `this.$on('blur')` work out of the box for example?)

## Investigate

- [ ] Running only some tests from command line
- [ ] Exposing configuration values to SCSS
- [ ] Exposing SCSS constants with JS
- [ ] Server-side rendering
	- Prerendering vs. true SSR

### Code intelligence and TypeScript

- [ ] VS Code IntelliSense
	- Great features out of the box for JS files. Needs more work to make work with `.vue` files.
	- Formatted comments?
	- Manifest files?
	- More workspace configuration?
	- Is there something we can do to improve the support?
	- VS Code still has troubles understanding Webpack aliases. `jsconfig.json` and `tsconfig.json` could be configured with the same aliases to make this work.
- [ ] Typing with Flow?
	- https://medium.freecodecamp.com/why-use-static-types-in-javascript-part-1-8382da1e0adb
	- https://flow.org/
	- https://alligator.io/vuejs/components-flow/
- [ ] TypeScript support
	- Integrate `.ts` support into pipeline
	- Integrate `.ts` support in Vue components, services, models...
	- Convert existing code into TS
	- Provide type hints etc.
	- https://vuejs.org/v2/guide/typescript.html

Makes code more robust, can improve IDE experience. Rapid iteration might get more complicated, introduces some more "boilerplate" code that needs to be manually maintained.

Some parts of the codebase, like models, utility libraries, state management, might benefit a lot from this. On the other hand simple single-file Vue components are mostly template and style-driven, and the view model code is almost never accessed by anything outside the component. Vue components have props (input), for which Vue has a validation feature.

TS features can be introduced gradually as features mature, but we still want to demo and try out new things fast without cumbersome code quality requirements (situation is similar with automated tests).

## Pipeline cleanup

### Configuration vs. build scripts

As a typical modern JavaScript system, Webpack is configured by scripting in JS. There are configuration values and other things that can be imported from separate configuration files to a larger extend than now. This way developers don't have to touch Webpack build scripts when making adjustments to things that are then fed to the build scripts rather than editing the script files directly, which tends to lead into accidental and hard-to-debug problems.

We already have config files under `src/config/`. These can also be imported by the application code, so that we have access to any configuration values also during run-time.

### Automation

Can we improve the pipeline to automate redundant tasks? Things such as the following cause a lot of boilerplate code that has to be manually maintained:

- [x] Importing and declaring child components
- [x] Importing and declaring directives used in components
- [x] Explicitly renaming child components locally
- [ ] Explicitly exporting components/directives/plugins/services/models in index files
- [ ] Explicitly importing services in each component
- [ ] Explicitly importing shared SCSS in `.vue` files
- [ ] Ensuring dependencies are up to date (directives and plugins imported in components must be installed via npm and `package.json` up to date)
- [ ] Webpack disallows dynamic requiring just like ES6 imports, but `require.context` could perhaps be used to improve automation
