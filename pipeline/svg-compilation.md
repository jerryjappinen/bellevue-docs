
# SVG compilation

```
src/
  |_ svg/
    |_ some-asset.svg
```

SVG assets are compiled into an SVG sprite with [external-svg-sprite-loader](https://www.npmjs.com/package/external-svg-sprite-loader).

SVGs are already a lightweight way to deliver image assets to the browser, but serving them in a sprite means they are all loaded with one HTTP request.

In the codebase, you refer to the original individual SVG assets like any other image. When you `require()` an SVG, the loader will return an object containing information needed to render an SVG element from the sprite.
