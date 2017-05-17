
# JavaScript coding conventions

We have predefined the coding style as much as possible with eslint. The rules are configured in `src/.eslintrc.js`.

## TL;DR

- Use tabs
- Use semicolons
- Use single quotes
- Declare vars one by one in the lowest scope as you use them, not in a batch
- Avoid arrow notation, just say `function`
- Write consistent code with `:` and `=`
- Use `import` rather than `require`
- Use `export` rather than `module.exports`

## Gotchas

### External dependencies

We use NPM for dependency management. As such, whenever you `import` an external dependency in your view component or JS file, the package has to be available locally. Your builds will fail until you have made the package available.

To ensure this, it has to be declared as a dependency in `package.json`. It is easy to just `npm install` a dependency locally but not store it in the manifest, in which case your own builds will work but others' won't.

When cleaning up these dependencies, nothing will fail when you forget to remove an external dependency from the manifest. However the dependency will still be installed as part of the package unnecessarily.

### Destructuring assignments in ES6

Although it is sometimes convenient, destructuring assigments are discouraged. It's better to try to write code that is consistent to all other types of assigments.

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

// The same eslint rule disallows this
var b = {
	a,
	...
};

// So let's just write this instead
var b = {
	a: a,
	...
};
```

Note that import/export syntax still sometimes requires curly braces, which is a separate use case.

See [this blog post](http://teeohhem.com/why-destructuring-is-a-terrible-idea-in-es6/) for a quick introduction.
