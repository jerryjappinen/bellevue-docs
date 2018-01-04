# Web fonts

## Hosted web fonts

To load fonts from Google Fonts or other providers, you need to simply get your app to load the provider's `.css` files that will in turn reference the web font files located on their servers. This is straight-forward to add in `config.paths.js`:

`src/config/config.paths.js`

```js
{
	//...

	styleLinks: [
		'//fonts.googleapis.com/css?family=Source+Sans+Pro:300,400,600|Roboto Mono|Dosis'
	],

	//...
}
```



## Local web fonts

Local web fonts are **not** preconfigured. Local font files are however easy to add to your project:

```
src/
	├── config/
	.	└── tooling/
	.		└── config.aliases.js
	├── fonts/
	.	└── my-font/
	.		├── myfont-extralightitalic.eot
	.		├── myfont-extralightitalic.ttf
	.		├── myfont-extralightitalic.woff
	.		├── myfont-extralightitalic.woff2
	.		├── myfont-light.eot
	.		├── myfont-light.ttf
	.		├── myfont-light.woff
	.		└── myfont-light.woff2
	└── styles/
		├── webfonts
		.	└── webfont-my-font.scss
		└── global.scss
```

To set up basic support:

1. Put your font files under `src/fonts/`
2. Add an alias `'@fonts': 'src/fonts'` in `src/config/tooling/config.aliases.js`

For each new font family:

1. Create a new SCSS file under `src/styles/fonts/`
2. Generate CSS the `font-face` declarations you need using the [`font-face` SCSS mixin](https://github.com/Eiskis/bellevue/tree/master/src/styles/mixins/mixin-font-face.scss)
3. `@import` the new SCSS file you created in `global.scss`

Example:

`src/styles/font-face/source-sans.scss`

```scss
@include font-face (
	'My Font',
	200,
	italic,
	'~@fonts/source-sans/myfont-extralightitalic'
);

@include font-face (
	'My Font',
	300,
	normal,
	'~@fonts/source-sans/myfont-light'
);
```

You can now refer to the included font family like any other font in your stylesheets, and expect users to have this font loaded when using the app.
