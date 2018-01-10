# Adding new assets

**How do I use icons, bitmap graphics and other assets?**

## Bitmaps

Add bitmap files anywhere under the `src/assets/` folder.

```
src/
	└── assets/
		└── some-dir/
			└── some-bitmap.png
```

Webpack will resolve any URLs you use to reference to these assets, but it's best to use aliases:

```js
var someBitmapPath = require('@assets/some-dir/some-bitmap.png');
```

```scss
.some-class {
	backgorund-image: url('~@assets/some-dir/some-bitmap.png');
}
```

```html
<!-- Raw img tag -->
<img :src="someBitmapPath">
<img src="~@assets/some-dir/some-bitmap.png">

<!-- Helper component (included) -->
<bitmap src="some-dir/some-bitmap.png" />
```

## SVG

```
src/
	└── svg/
		├── MyAsset.svg
		└── index.js
```

Add your SVG in the `src/svg/` and `src/svg/index.js`. Webpack will read the SVG and turn it into a Vue component you can use in your code:

```html
<!-- Generated SVG component (included) -->
<svg-my-asset />

<!-- Helper component (included) -->
<vector src="my-asset" />
```
