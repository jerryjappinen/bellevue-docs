
# Creatinbg transitions and animations

```
src/
  |_ styles/
  	|_ transitions/
  	  |_ transition-foo.scss
```

- Vue guides for transitions: [vuejs.org/v2/guide/transitions](https://vuejs.org/v2/guide/transitions) (includes advanced topics)

Vue has built-in `<transition>` components which trigger transition-oriented classnames on elements when they are removed or added to the DOM. This allows easily defining reusable named transitions, or simply adding the necessary CSS for each state class in your component code.

It's preferred to write reusable named transitions. For common use cases, a named transition looks something like this:

`src/vue-components/MyComponent.vue`

```html
<transition name="transition-fade">
	<div v-if="condition"></div>
</transition>
```

`src/styles/transitions/transition-fade.scss`

```scss
.transition-fade-enter-active,
.transition-fade-leave-active {
	opacity: 1;
	transition: opacity 0.25s;
}

.transition-fade-enter,
.transition-fade-leave-to {
	opacity: 0;
}
```

Vue also exposes JavaScript hooks for advanced transition code.

## Transitions for routes

This is similar to any other conditional rendering case. Simply use `<transition>` with like you would with, for example, `v-if`, and you're good.

```html
<transition name="transition-fade">
	<router-view></router-view>
</transition>
```

## Keyframe animations

**The preferred way** is to add reusable `@keyframes` definitions under `src/styles/keyframes/`.

If that doesn't make sense, declare a `@keyframes` animation in your component code. If you do this, just prefix your animation name with `view-<viewname>-`.

In either case, when your keyframe animation is declared, it can be used as the `animation-name` in your (S)CSS.
