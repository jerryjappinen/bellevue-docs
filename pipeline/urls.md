
# URL resolution and aliases

Webpack will resolve URLs for you. You can use relative URLs in any context (importing, HTML assets, CSS etc.) to point to a specific file from the specific file you are writing the URL in.

We can also use aliases though, so that you don't always have to keep track of the relative positioning of specific source files (which easily leads to bugs when refactoring).

Aliases are configured here:

```
src/
  |_ config.js
```

Use aliases like so:

JavaScript:

```js
import config from '@config.js';
var imgPath = require('@assets/logo.png');
```

HTML and `.vue` templates:

```html
<img src="~@assets/logo.png">
```

SCSS:

```scss
@import '~@styles/shared';
.foo {
	background-image: url('~@assets/logo.png');
}
```

Aliases work in `.vue` files as well as standalone JS/SCSS/HTML files.
