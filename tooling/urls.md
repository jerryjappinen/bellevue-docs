
# URL resolution and aliases

Webpack will resolve URLs for you. You can use relative URLs in any context (importing, HTML assets, CSS etc.) to point to a specific file from the specific file you are writing the URL in.

We can also use aliases though, so that you don't always have to keep track of the relative positioning of specific source files (which easily leads to bugs when refactoring).

Aliases are configured here:

```
src/
	|_ config/
		|_ config-aliases.js
```

## Using aliases

JavaScript (**no** `~` prefix):

```js
import config from '@config';
var imgPath = require('@assets/logo.png');
```

HTML (**with** `~` prefix):

```html
<img src="~@assets/logo.png">
```

SCSS (**with** `~` prefix):

```scss
@import '~@shared-styles';
.foo {
	background-image: url('~@assets/logo.png');
}
```

Aliases work in `.vue` files as well as standalone JS/SCSS/HTML files.