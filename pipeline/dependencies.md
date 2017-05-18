
# Dependency management

All the dependencies of both the pipeline and the application code are managed by node and Webpack. Dependency management can handle modules (`module.exports = {}` and `require()`) or ES6 `import`/`export`.

Internal or external Dependencies declared in any `.vue`, `.scss` or `.js` file will be resolved by Webpack and node.

External dependencies required for client builds **need to also be declared in `package.json`** under `dependencies: {}`. These should also be cleaned up when a dependency is no longer needed.

```js
// Import external dependency directly
// Needs to be installed via NPM
// Should have been saved in package.json via npm install lodash --save
import _ from 'lodash';

// Import internal dependency
import Role from '@models/Role';
import Spinner from '@components/snippets/Spinner';

// You can even import styles in a .vue component
import '@styles/global';
import '@styles/utilities';
```

```scss
// Import internal dependency
@import '~@styles/shared.scss';
```

Currently there is no magical globals configured for JavaScript and no magical base CSS injected outside the components.
