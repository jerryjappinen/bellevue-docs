
# Utilities

```
src/
  |__ util/
    |__ util-something.js
```

Utils are custom libraries of common functions that could just as well be external libraries.

They are only included as integrated libraries and not published separately mostly for convenience and the fact that they are written for specific needs instead of providing a full-fledged experience as an external library to other developers.

Utilities are **not** Vue objects. Change detection in them is not enabled and you cannot use things like computed properties or the Vue object lifecycle. If you need change detection, you probably want to write a [service](services.md) instead.
