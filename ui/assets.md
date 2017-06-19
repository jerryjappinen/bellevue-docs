
# SVG and bitmap assets

```
src/
	├── assets/
	.	└── logo.png
	└── svg/
		└── some-asset.svg
```

## Bitmap and static assets

You can use the assets under the asset folder normally in HTML, CSS and JS. Just use aliases to robustly refer to the right path regardless of the source file location:

```html
<img src="~@assets/logo.png">
```

## Using SVGs from SVG sprite

This project template comes with tooling that compiles SVGs into sprites automatically. It's most convenient and robust to render SVG with a dedicated component so you don't need to worry about the details when using SVG assets in your views.

**Example:** [`<pic-svg>`](https://github.com/Eiskis/bellevue/blob/master/src/components/snippets/PicSvg.vue)

_Any_ SVG is simply XML, and can be styled with CSS:

```scss
.view-my-component {
	.view-pic-svg {
		fill: $color-red;
	}
}
```

_Some_ SVGs are designed to be dynamically colored with the current text color:

```scss
.view-my-component {
	color: $color-red;
	// no need to specify any SVG parameters
}
```

The designer has chosen how and which parts of the icon to apply this `currentColor` to. It might color the entire fill of the icon, or one or two strokes. Different elements in the icon might have also different opacities even if they use `currentColor`, resulting in the final rendered icon appearing as multicolor.

[Read more about SVG compilation](../tooling/svg-compilation.md)

## Generated SVG

SVG code can be generated directly in a Vue component. This is not very convenient most of the time, but can be used to generate dynamic SVG graphics such as spinners and progress bars.

**Example:** [`<spinner>`](https://github.com/Eiskis/bellevue/blob/master/src/components/snippets/Spinner.vue)
