
# SVG and bitmap assets

```
src/
  |_ assets/
    |_ logo.png
  |_ svg/
    |_ some-asset.svg
```

## Bitmap and static assets

You can use the assets under the asset folder normally in HTML, CSS and JS. Just use aliases to robustly refer to the right path regardless of the source file location:

```html
<img src="~@assets/logo.png">
```

## Using SVGs from SVG sprite

The pipeline compiles SVGs into sprites automatically. It's most convenient and robust to render SVG with a dedicated component so you don't need to worry about the details when using SVG assets in your views.

**Example:** [<pic-svg>](https://github.com/Eiskis/vue-webpack/blob/master/src/vue-components/snippets/PicSvg.vue)

SVGs are XHTML and can be styled with CSS.

```scss
.view-my-component {
	.view-pic-svg {
		fill: $color-red;
	}
}
```

## Generated SVG

SVG code can be generated directly in a Vue component. This is not very convenient most of the time, but can be used to generate dynamic SVG graphics such as spinners and progress bars.

**Example:** [<spinner>](https://github.com/Eiskis/vue-webpack/blob/master/src/vue-components/snippets/Spinner.vue)
