
# Utilities

```
src/
    |_ util/
        |_ util-something.js
```

Utils are custom libraries of common functions that could just as well be external libraries.

They are only included as integrated libraries instead of published externally for convenience. They are written for specific needs instead of providing a full-fledged experience as an external library to other developers, and publishing them as standalone libraries will always need a bit more polishing.

Utilities are **not** Vue objects. Change detection in them is not enabled and you cannot use things like computed properties or the Vue object lifecycle. If you need to write shared functionality with, you probably want to write a [service](services.md) instead.
