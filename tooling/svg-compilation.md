# SVG compilation

```
src/
	└── svg/
		├── MyAsset.svg
		└── index.js
```

SVG assets are compiled into Vue components with [`vue-svg-loader`](https://www.npmjs.com/package/vue-svg-loader). SVGs are already a lightweight way to deliver image assets to the browser, but this pipeline will also optimize them with [SVGO](https://github.com/svg/svgo). SVGO parameters can be adjusted in [`config/svgo.js`](https://github.com/Eiskis/bellevue/blob/master/src/config/tooling/svgo.js).

Any SVG exported in `src/svg/index.js` will be registered as a Vue component. You can organize your files into directories freely, but when exported each asset should have a unique name.

You can use each SVG in your components either directly (`<svg-my-asset />`) or with the included `Vector` (`<vector src="my-asset" />`).

## Colored icons with `currentColor`

SVG elements can be dynamically colored like any other HTML element by setting a color attribute to `currentColor`. This makes it easy to reuse the same assets when using icons in the app.

Setting SVG color values to `currentColor`is tricky with graphics software like Sketch, but SVGO can easily replace a placeholder color value with it. During compilation, any color attribute with the value `#FF00FF` will be replaced with currentColor. These attributes will then be rendered with the value of CSS `color` in any given context.

In practice, these icons have the same color as the text.

The placeholder value can be customized in the SVGO configuration.
