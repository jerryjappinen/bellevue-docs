# Misc. notes and evaluations

## Stack

### Vue

- Excellent guides and documentation at [vuejs.org](https://vuejs.org/v2/guide/).
- Curated list of awesome things related to Vue.js available at [GitHub](https://github.com/vuejs/awesome-vue).
	- [Components and libraries](https://github.com/vuejs/awesome-vue#components--libraries)

### Webpack

- Webpack seems to understand the codebase very well and enable a lot of very advanced features.
- A lot of imports have to be (manually) maintained to enable this though
- Only seems to need restarting when core config is updated, otherwise recompiling and hot reload work out of the box very reliably
- `vue-loader` is the thing that sits between `.vue` single file components and Webpack, which should be extended for component-specific things
- Extending Webpack seems like a viable option for further automation in codebase
	- Automating `.js` imports
	- Automating `.scss` @imports
	- Generating stats/reports (on automated features)?

### Coding conventions

- Based on the official Webpack project structure
	- https://github.com/vuejs-templates/webpack
	- Vuex support has been added
	- Non-trivial global SCSS styles have been added (loaded by root component)
	- Running tests in Chrome instead of PhantomJS (this is easily configurable)
	- Custom components showcasing common patterns and features added
- Linting is extensively supported and has been has been configured
	- ESLint for JavaScript: http://eslint.org/
	- Styleling for (S)CSS
	- htmllint for HTML (only one `.ejs` file in project which is not linted)
	- These all work in IDEs, terminal, and also within `.vue` files (with only one minor issues: linters report wrong line numbers)
- Other conventions
	- Defaults in component properties and methods
		- Try to set boolean defaults to false.
		- Developers then know that in order to change default behavior, they have to explicitly set something to true.

### TypeScript

- Could be very useful in models and separate utilities.
- Requires some extra setup work to play nicely with Webpack aliases and Vue components.
- Vue components have to be written in a certain way to work with TS.
- Vue components are generally very simple, so TS usefulness is limited.
- We already have linting for all languages and some level of IntelliSense in VS Code available.
- Most functionality depends on run-time stuff, how useful will TS be with Vue?

# Project features

## Existing features

- Linting via CLI and Webpack
- Per-environment configuration
	- See `config/`
- Vue and all its goodies
	- Named transitions with JS callbacks
	- Prop validation
- Single file components as `.vue` files
	- Standard HTML, CSS and JS
- Solution for including Vue plugins
	- Example: https://github.com/foxbenjaminfox/vue-async-computed
	- Example: https://github.com/scaccogatto/vue-throttle-event
	- Split route config and store from the actual plugin loading
- Solution in pipeline for including Vue directives
	- Example: https://github.com/David-Desmaisons/Vue.ImagesLoaded
	- Example: https://www.npmjs.com/package/vue-keep-scroll-position
- Routing
	- Easy-to-configure named routes
	- Multilevel routes out of the box
	- Selected page comparison and highlight
- Development vs. production modes
	- http://vuejs-templates.github.io/webpack/env.html
- Developer tools
	- Amazing hot reload for development
		- No browser plugin needed
		- Super fast
		- Preserves state, swaps components real time
		- Shows ESLint errors
		- https://webpack.js.org/concepts/hot-module-replacement/
	- Vue developer plugin for Chrome
	- Detailed console errors from Vue
- Tests
	- Can be run on multiple browsers
	- Unit tests for components and Vuex
		- `test/unit/`
		- http://vuejs-templates.github.io/webpack/unit.html
	- E2E tests
		- `test/e2e/`
		- http://vuejs-templates.github.io/webpack/e2e.html
- Web fonts
- Resolving asset URLs
	- http://vue-loader.vuejs.org/en/configurations/asset-url.html
- CSS pipeline
	- CSS extraction for most popular CSS pre-processors (LESS, SASS, Stylus, and PostCSS)
	- To use a pre-processor, all you need to do is installing the appropriate Webpack loader for it
	- Autoprefixing included
	- http://vuejs-templates.github.io/webpack/pre-processors.html
	- SCSS and global styling structure added (mixins, custom functions etc.)
	- More features: http://vue-loader.vuejs.org/en/ (scoped styles etc.)
- HTML cleanup
	- Comments => gone
- SVG pipeline
	- Optimization and cleanup with SVGO
	- Sprites usable with URL resolving
	- Dedicated component
- [Vuex](http://vuex.vuejs.org/en/intro.html) for state management
	- Trivial counter app example: [jsfiddle.net/n9jmu5v7/341](https://jsfiddle.net/n9jmu5v7/341/)
	- More complex example: https://github.com/vuejs/vuex/tree/dev/examples/shopping-cart
- `browserslist` in package.json
	- Used by Autoprefixer in PostCSS
	- Can further be used by linters to warn for incompatible code
- (S)CSS linting
	- Works on command line
	- Works for global `.scss` and `.vue` files
	- Cascading configuration
	- https://stylelint.io/
	- https://github.com/vuejs/vue-loader/issues/303#issuecomment-259328193
	- https://medium.com/lost-bananas/linting-css-in-vue-files-6bb20faac0f2
- Values imported and treated from custom configuration file
	- When making edits, developers are not touching delicate configuration scripts
- Route-specific meta tag handling
	- https://github.com/vuejs/awesome-vue#meta-tags
	- Doesn't have to be a Vue-specific library
- Separate business logic models as viewless Vue objects
	- Simple to encapsulate non-view-specific business logic as objects (accounts, roles etc.)
	- They also inherit plugins loaded into Vue


## Missing features

### Missing client-side

- Offline handling
	- Requires some manifest files etc. plus UI work
- Input validation
	- `vue-validator`
- Vue directives
	- Simple to add via `main.js`
	- Rarely needed though
- Backend integration, authentication and fetching data
	- `vue-resource`
	- http://vuejs-templates.github.io/webpack/backend.html
	- http://vuejs-templates.github.io/webpack/proxy.html
	- https://router.vuejs.org/en/advanced/data-fetching.html
- Custom Vue plugins
	- Relatively easy to create
	- https://vuejs.org/v2/guide/plugins.html
- Localisation
	- https://github.com/vuejs/awesome-vue#i18n
- Persistent state
	- Works for services
	- Trivial to add for Vuex
- Authentication
	- https://github.com/vuejs/awesome-vue#authenticationauthorization
- Splitting global state management
	- Vuex supports modules
	- Multiple stores?
	- What are the best practices for this? Need to look at a real application

### Problems/missing in pipeline

- The state of modern web development: the whole pipeline is a delicate flower
- `htmllint` is not integrated with Webpack 2 yet
- App icons for multiple platforms, devices etc.
	- Maybe not needed
- Manifest file generation
	- Caches and offline stuff
	- Web app manifests
	- robots.txt
	- etc.
- Server-side rendering
	- Prerendering plugin for this pipeline: http://vuejs-templates.github.io/webpack/prerender.html
	- About SSR on Vue: https://vuejs.org/v2/guide/ssr.html
	- Full SSR guide for Vue: https://ssr.vuejs.org/en/
	- Universal apps on Vue: https://nuxtjs.org/
- Additional ESLint plugins for enhanced IDE integration
	- File name and export naming conventions: https://github.com/selaux/eslint-plugin-filenames
	- Curated list of what's out there: https://github.com/dustinspecker/awesome-eslint
	- https://github.com/amilajack/eslint-plugin-compat
	- https://github.com/sheerun/prettier-standard

Did not test E2E, needs a JDK installed in order to be run from the command line.

### Missing examples

- Unit tests for custom components



## Questions

- Need to write more about coding conventions to make code reviews painless
	- Linting is a big help
	- Tests help, but what kind of tests should we write?
- What are the most relevant practical sample projects we should look at?
	- https://vuejs.org/v2/examples/
- How complex should we make global state management?
	- Services work very nicely
	- There are many standard alternatives: https://github.com/vuejs/awesome-vue#state-management
	- But Vuex is the "official" solution
	- Vuex integrates into Vue dev tools
	- "If you’re coming from React, you may be wondering how vuex compares to redux, the most popular Flux implementation in that ecosystem. Redux is actually view-layer agnostic, so it can easily be used with Vue via some simple bindings. Vuex is different in that it knows it’s in a Vue app. This allows it to better integrate with Vue, offering a more intuitive API and improved development experience."
- Could SCSS be tested somehow?
	- We have some more complicated toolchains producing utility classes with responsive variants etc.
	- http://mts.io/2014/04/02/sass-unit-testing/
	- Also need a test page for quick manual visual testing
- Can we improve the pipeline to automate redundant tasks
	- Importing and declaring child components
	- Importing and declaring directives used in components
	- Explicitly renaming child components locally
	- Importing shared SCSS in `.vue` files
	- Ensuring dependencies are up to date (directives and plugins imported in components must be installed via npm and `package.json` up to date)
	- Webpack disallows dynamic requiring just like ES6 imports, but `require.context` could perhaps be used to improve automation
- What should our conventions be?
	- We have a project structure and pipeline: but how do we use it effectively to write good UIs that scale?
- How does API communication and resource loading work?
	- Should we use [`vue-resource`](https://github.com/pagekit/vue-resource)?
	- HTTP is not a problem
	- Writing models is not a problem
	- Should we use a more high-level REST library?
	- Should there be a tighter coupling or a wrapper API library we write for out API?
	- GraphQL?
- Should we add more PostCSS functionality?
	- http://postcss.parts/


# IDE integration

- Browser will show errors the same way regardless of IDE
- Sublime Text
	- Linting experience is quite good with Sublime Linter and its extensions
	- Easy setup
	- Lightweight development experience
- Visual Studio Code
	- TL;DR
		- Great support for modern web development
		- Easy set-up
		- Fast iteration cycles, meaningful updates month-over-month
		- Well equipped for TS support
	- Adjusted keybindings
		- Mostly to match Sublime Text better
		- Line up/down
		- Increment and decrement
		- Debug/launch without `F` keys
	- Theming supported well
		- Color schemes supported out of the box
		- Multiple color schemes available out of the box
		- Live preview for color schemes
		- File icons in sidebar disabled by default
		- Install more themes from commands
	- IntelliSense
		- Already get some inline documentation, snippets and parameters
		- Further configuration might be required for full support (component names, props etc.)
	- Problems
		- Does not auto indent new lines when starting from empty non-intended line inside a block
		- Can't yet show all problems in the project at once (only open files)
			- See https://github.com/Microsoft/vscode/issues/13953
			- Linters will of course show all issues in terminal/browser
- Need to investigate WebStorm
