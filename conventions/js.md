
# JavaScript coding conventions

We have predefined the confing style as much

## TL;DR

- Use tabs
- Use semicolons
- Avoid arrow functions
- Write consistent code that doesn't spare `:` and `=`
- Use `import` rather than `require`
- Use `export` rather than `module.exports`

## Gotchas

### External dependencies

We use NPM for dependency management. As such, whenever you `import` an external dependency in your view component or JS file, the package has to be available locally. Your builds will fail until you have made the package available.

To ensure this, it has to be declared as a dependency in `package.json`. It is easy to just `npm install` a dependency locally but not store it in the manifest, in which case your own builds will work but others' won't.

When cleaning up these dependencies, nothing will fail when you forget to remove an external dependency from the manifest. However the dependency will still be installed as part of the package unnecessarily.

### Destructuring assignments in ES6

Although it is sometimes convenient, destructuring assigments are discouraged.

```js
var a = {
	foo: 123,
	bar: 'Some string'
};

// Do this
var someVar = a.foo;

// Don't do this
{ foo: someVar } = a;

// The same rules disallow this
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
