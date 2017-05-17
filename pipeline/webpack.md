
# Webpack

## Environments

The current pipeline supports three distinct environments:

- `dev`
- `prod`
- `test`

## Environments and cascading configuration

The build/serve/run routines executed are obviously different in each environment. Webpack config is split into base config and environment-specific config. The latter intuitively extends the former one. The config files are available under `build/`

## Loaders

- [vue-loader](http://vue-loader.vuejs.org/en/) loads `.vue` files
- [sass-loader]() loads `.scss` files
- [postcss-loader]() loads CSS files
