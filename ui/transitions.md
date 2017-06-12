
# Creating transitions and animations

```
src/
    |_ styles/
  	    |_ transitions/
  	        |_ transition-foo.scss
```

- Vue guides for transitions: [vuejs.org/v2/guide/transitions](https://vuejs.org/v2/guide/transitions) (includes advanced topics)

Vue has built-in `<transition>` components which trigger transition-oriented classnames on elements when they are removed or added to the DOM. This allows easily defining reusable named transitions, or simply adding the necessary CSS for each state class in your component code.

The `mode` attribute defines the "playback" order of animations. If you're switching between two elements, usually `mode="out-in"` is what you want.

In short this means that Vue lets you easily define how to transition elements with conditional rendering. Note that Vue often needs you to define a `key` attribute for elements (it's like a unique ID). You can also declare dynamic values for keys, and any time a key changes, Vue will transition the element out with old values and in again with new, changed values.

It's preferred to write reusable named transitions. For common use cases, a named transition looks something like this:

`src/components/MyComponent.vue`

```html
<!-- Example: transitioning between two elements -->
<transition name="transition-fade" mode="out-in">
	<div v-if="condition" key="someKey"></div>
	<div v-else key="someOtherKey"></div>
</transition>

...

<!-- Example: dynamic key (here the effect would be a clock fading in and out when time updates) -->
<transition name="transition-fade">
	<div :key="currentTime">
		{{ currentTime }}
	</div>
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

**The preferred way** is to add reusable `@keyframes` definitions under `src/styles/keyframes/` (remember to also import new files in `global.scss`).

If that doesn't make sense, declare a `@keyframes` animation in your component code. If you do this, just prefix your animation name with `view-<viewname>-`.

In either case, once your keyframe animation is declared, it can be used as the `animation-name` in your either global styles or component styles.
