# Web fonts

## Hosted web fonts

To load fonts from Google Fonts or other providers, you need to simply get your app to load the provider's `.css` files that will in turn reference the web font files located on their servers. This is straight-forward to define in `config.paths.js`:

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

```
src/
	├── fonts/
	.	├── myfont-regular.eot
	.	├── myfont-regular.ttf
	.	├── myfont-regular.woff
	.	├── myfont-regular.woff2
	.	├── myfont-regular-italic.eot
	.	├── myfont-regular-italic.ttf
	.	├── myfont-regular-italic.woff
	.	├── myfont-regular-italic.woff2
	.	├── myfont-bold.eot
	.	├── myfont-bold.ttf
	.	├── myfont-bold.woff
	.	├── myfont-bold.woff2
	└── styles/
		└── constants.scss
```

Bellevue can generate `@font-face` definitions for any web fonts that you wish to deliver in your application package. This is crucial for offline apps, for example. You only need to define which fonts you want to use in `constants.scss`:

```scss
$local-web-fonts: (
	(
		font-family: 'My Font Family',
		font-weight: 400,
		font-style: normal,
		filename: 'myfont-regular',
	),
	(
		font-family: 'My Font Family',
		font-weight: 400,
		font-style: italic,
		filename: 'myfont-regular-italic',
	),
	(
		font-family: 'My Font Family',
		font-weight: 700,
		font-style: normal,
		filename: 'myfont-bold',
	),
);
```

The [global styling pipeline](https://github.com/Eiskis/bellevue/tree/master/src/styles/global.scss) will use a mixin to generate the `@font-face` rules based on your definition here. You can thus expect users to have this font loaded when using the app and use the font family in your stylesheets.
