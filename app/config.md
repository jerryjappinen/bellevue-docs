
# Centralised configuration

```
src/
	└── config/
		├── config.aliases.js
		├── config.base.js
		├── config.routes.js
		└── config.styles.js
```

This template has carefully been set up so that various parts of the tooling as well as app code pull configurable values from one place. Generally speaking the developer doesn't have to edit Webpack script files while setting up a new project, or doing regular application development (like defining routes).

Configuration is spread accross multiple files:

- [`config.base.js`](https://github.com/Eiskis/bellevue/blob/master/src/config/config.base.js) is the general-purpose config file which is most commonly edited.
- [`config.routes.js`](https://github.com/Eiskis/bellevue/blob/master/src/config/config.routes.js) includes all route configuration.
- [`config.aliases.js`](https://github.com/Eiskis/bellevue/blob/master/src/config/config.aliases.js) defines Webpack aliases that can be used for [URL resolution](../tooling/urls.md).
- [`config.styles.js`](https://github.com/Eiskis/bellevue/blob/master/src/config/config.styles.js) will pull variables from `constants.scss` automatically and so you can access them in JavaScript.

## Accessing config in application code

Anywhere in your application, you can import the extended configuration and use it to trigger any behavior you want.

```js
import config from '@config';
console.log(Object.keys(config));
// [ 'defaultLocale', 'fallbackLocale', 'meta', 'mobile', 'routes', 'styles', ... ]
```

## Environment variables for build scripts

Some of the build scripts accept environment variables for setting things like the development server port or test driver. The supported variables and examples of how to set them are [listed on the setup page](../overview/setup.md).
