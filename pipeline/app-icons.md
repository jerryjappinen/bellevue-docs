
# App icon generation

```
src/
  |__ app-icon/
    |__ app-icon.png
```

Webpack can generate app icons for multiple target platforms from a single source file. This can be quite slow however and enabling this can add significantly to the development environments startup time, although they won't be regenerated during normal development unless the source file changes.

**Note:** This feature is implemented in a crude form but is still lacking. To enable this feature, uncomment the part where `FaviconsWebpackPlugin` is used in `webpack.base.conf.js`.
