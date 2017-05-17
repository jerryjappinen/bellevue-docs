
# Creatinbg transitions and animations

## Transitions for conditional rendering

...

You can opt to use reusable named transitions, or simply add the necessary CSS for each state class in your component code.

## Transitions for routes

This is similar to any other conditional rendering case. Simply use `<transition>` like you would with, for example, `v-if`, and you're good.

## Animations

**The preferred way** is to add reusable `@keyframes` definitions under `src/styles/keyframes/`.

If that doesn't make sense, declare a `@keyframes` animation in your component code. If you do this, just prefix your animation name with `view-<viewname>-`.
