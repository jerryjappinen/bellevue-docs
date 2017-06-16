
# Web fonts

```
src/
	|_ fonts/
		|_ some-font/
			|_ some-font-regular.ttf
			|_ some-font-regular.woff
			|_ some-font-bold.ttf
			|_ some-font-bold.woff
	|_ styles/
		|_ webfonts
			|_ webfont-some-font.scss
		|_ global.scss
```

## Local web fonts

Local web fonts are fairly easy to add to the app:

1. Put your font files under `src/fonts/`
2. Create a new SCSS file under `src/styles/webfonts/`
3. Generate CSS `font-face` declarations for the font files with the [`font-face` SCSS mixin](https://github.com/Eiskis/bellevue/tree/master/src/styles/mixins/mixin-font.scss) like in [this example](https://github.com/Eiskis/bellevue/tree/master/src/styles/webfonts/webfont-source-sans.scss).
4. `@import` the new webfont SCSS file in `global.scss`

You can now refer to the included font family like any other font in your stylesheets, and expect users to have this font loaded when using the app.

## Hosted web fonts

If you prefer to use a hosted service like _Google Fonts_, you might retrieve the CSS definitions from the hosted service instead of including it in the global styles. These should be included just like any other vendor stylesheet links, i.e. by adding them as `<link>` tags in `index.html.ejs`. You can then use the font name as `font-family` in your CSS like with any other font.
