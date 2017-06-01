
# Adding new assets

## Bitmaps

Add bitmap files anywhere under the `src/assets/` folder.

```
src/
  |_ assets/
    |_ some-dir/
      |_ some-bitmap.png
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
<img :src="someBitmapPath">
<img src="~@assets/some-dir/some-bitmap.png">
```

## SVG

```
src/
  |_ svg/
    |_ some-asset.svg
```

Add your SVG in the `src/svg/`. Webpack pipeline will pick it up from here and [compile it into a sprite](../pipeline/svg-compilation.md). It can then be used with one of the `<pic>` components.

```html
<pic-svg :asset="some-asset"></pic-svg>
```
