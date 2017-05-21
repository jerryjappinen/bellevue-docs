
# SVG compilation

```
src/
  |_ svg/
    |_ some-asset.svg
```

SVG assets are compiled into an SVG sprite with [external-svg-sprite-loader](https://www.npmjs.com/package/external-svg-sprite-loader).

SVGs are already a lightweight way to deliver image assets to the browser, but serving them in a sprite means they are all loaded with one HTTP request.

In the codebase, you refer to the original individual SVG assets like any other image. When you `require()` an SVG, the loader will return an object containing information needed to render an SVG element from the sprite.

## Optimization

SVG icons are passed through [SVGO](https://github.com/svg/svgo) during compilation. SVGO parameters can be adjusted in [src/config.base.js](https://github.com/Eiskis/vue-webpack/blob/master/src/config.base.js).

## Colored icons with currentColor

SVG elements can be dynamically colored like any other HTML element by setting a color attribute to `currentColor`. This makes it easy to reuse the same assets when using icons in the app.

Setting SVG color values to `currentColor`is tricky with graphics software like Sketch, but SVGO can easily replace a placeholder color value with it. During compilation, any color attribute with the value `#FF00FF` will be replaced with currentColor. These attributes will then be rendered with the value of CSS `color` in any given context.

In practice, these icons have the same color as the text.

The placeholder value can be customized in the SVGO configuration.
