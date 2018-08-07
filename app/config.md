# Centralised configuration

```
src/
	config/
		├── dev/                    // Config overrides for development mode
		.	├── analytics.js
		.	├── build.js
		.	├── meta.js
		.	├── paths.js
		.	├── router.js
		.	└── styles.js
		.
		├── tooling/                // Configuration that won't be available runtime
		.	├── aliases.js      // Webpack aliases
		.	├── manifest.js
		.	├── robotsTxt.js
		.	├── routes.js       // Routes
		.	├── sitemap.js
		.	└── svgo.js
		.
		├── analytics.js
		├── build.js
		├── meta.js                 // Meta information (app title, description etc.)
		├── paths.js
		├── router.js
		└── styles.js
```

Various parts of the tooling as well as your runtime code pull configurable values from one place. Generally speaking, as a developer you don't have to edit Webpack script files while setting up a new project or during everyday app development.

Configuration is spread accross multiple files, and you can easily override some of them for your development environment only. It's also easy to add more configuration files here for any custom configuration or new Webpack plugins.

## Accessing config in runtime code

Anywhere in your application, you can import the configuration using the `@config` alias.

```js
import buildConfig from '@config/build'
console.log(buildConfig)
// { isDebug: false, offline: false }
```

Note that in development mode, `@config` will point to `src/config/dev/` while in production it points to `src/config/`.

## CLI environment variables

You can change the port of your development server by setting an environment variable for your npm script. [See the setup instructions](../overview/setup.md) for an example.
