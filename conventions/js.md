
# JavaScript coding conventions

The coding style of the application code is defined as closely as possible with ESLint. The rules are configured and annotated in:

```
src/
	└── .eslintrc.js
```

## TL;DR

- Use tabs, semicolons, single quotes.
- Declare vars one by one in the lowest scope as you use them, not in a batch.
- Avoid arrow notation; use `function` to avoid any gotchas with `this` or unclear syntax.
- Write consistent code with `:` and `=`, avoid mixing typical assignment syntax with unclear object shorthands.
- Use `import` rather than `require`.
- Use `export` rather than `module.exports`.

## Gotchas

### External dependencies

We use NPM for dependency management. As such, whenever you `import` an external dependency in your view component or JS file, the package has to be available locally. Your builds will fail until you have made the package available.

To ensure this, it has to be declared as a dependency in `package.json`. It is easy to just `npm install` a dependency locally but not `--save` it, and thus not store it in the manifest. In this case your own builds will work but for other developers they won't.

**Note:** When Node 8 was released, so was npm 5, which changed `--save` to be the default. There's no harm in using the parameter explicitly though.

When cleaning up these dependencies, nothing will fail when you forget to remove an external dependency from the manifest. However the dependency will still be installed as part of the package unnecessarily.

**Quick tip:** to search for all non-internal imports in Visual Code Studio, use the search with the regular expression `from '[^\.~@]`. This will find all JavaScript imports that don't use one of the aliases or a relative path.

### `export`/`import`

ES6 export/import syntax is sometimes a little bit weird. It's not always easy to tell what variable name is being imported into the current scope, and what assumption is made about the export names used by the dependency.

Given the following fairly common setup in `someFile.js`

```js
var foo = 'foo';
var bar = 'bar';

// Named export syntax
export {
	foo,
	bar
};

// Object shorthand
export default = {
	foo,
	bar
};
```

In `anotherFile.js`:

```js
// Will import the default as a new variable "foo"
// The value of foo in the original would be under "foo.foo"
import foo from 'someFile.js';

// Will import foo as a new variable "foo"
import { foo } from 'someFile.js';

// Will import foo as a new variable "someVar"
import { foo as someVar } from 'someFile.js';
```

It's easy to mix these up since the import/export is so similar to normal object assignment syntax. It's a different language feature however.

### Object shorthands

Object shorthands are a bit magical, but they are consistent with `export`/`import` syntax and save some boilerplate code in many situations without making things much less clear:

```js
// You don't have to write this
var b = {
	foo: foo,
	bar: bar
};

// This is ok
var b = {
	foo,
	bar
};
```

### Destructuring assignments in ES6

Destructuring assigments are **discouraged**. It's often very unclear, and inconsistent with other types of assigments.

See [this blog post](http://teeohhem.com/why-destructuring-is-a-terrible-idea-in-es6/) for a quick introduction.

```js
// Given the following
var a = {
foo: 123,
bar: 'Some string'
};

// Do this
var someVar = a.foo;

// Don't do this
{ foo: someVar } = a;
```
