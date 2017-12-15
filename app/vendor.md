
# Vendor code

Vendor code is `imported` via `npm`. You can install any library you wish and then import it in any component, service, model or utility. The dependencies are defined and maintained in `package.json`.

**Note:** remember that every vendor library you import will increase the size of your codebase and make it slower to load for the end-user.

**Note:** remember to remove any libraries you no longer use from your `package.json`.

**Note:** when installing, remember to `--save-dev` any dependencies you only need for tooling and not for client-side application code.

## Example

Dependencies must be installed and stored in `package.json` before they can be used in the codebase.

```sh
npm install lodash --save
```

After this, you can use what you installed in your application code.

```js
import _ from 'lodash';
var foo = _.trim(' Foo     ');
```

## Initial setup for vendor code

```
src/
	└── vendor/
		└── Chart.js
```

Sometimes you want to do some common setup work when using a vendor library throughout your application. In this case, add an intermediate wrapper file under `@vendor` and import the vendor code from there.

`src/vendor/Chart.js`

```js
// Import library from NPM
import Chart from 'chart.js'

// One-time setup work
Chart.defaults.global.defaultFontColor = '#000000'

// Export the modified vendor library
export default Chart
```

Use vendor library in your code:

`src/components/MyComponent.vue`

```js
import Chart from '@vendor/Chart';
```
