
# Centralised configuration

```
src/
	config/
		config-aliases.js
		config-base.js
		config-routes.js
		config-styles.js
```

This template has carefully been set up so that various parts of the tooling as well as app code pull configurable values from one place. Generally speaking the developer doesn't have to edit Webpack script files while setting up a new project, or doing regular application development (like defining routes).

Configuration is spread accross multiple files. `config-base.js` and `config-routes.js` are the ones most commonly edited. `config-styles.js` will pull variables from `.scss` automatically and allow you to access them in JavaScript without duplicating the values.

## Configuration format

Here are the default values for the base configuration.

```js
{% include "git+https://github.com/Eiskis/bellevue.git/config/config-base.js" %}
```

## Accessing config in application code

Anywhere in your application, you can import the extended configuration and use it to trigger any behavior you want.

```js
import config from '@config';
console.log(Object.keys(config));
// [ 'defaultLocale', 'fallbackLocale', 'meta', 'mobile', 'aliases', 'routes', 'styles', ... ]
```
