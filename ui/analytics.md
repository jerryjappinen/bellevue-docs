# Analytics

## Google Analytics

Google Analytics is preconfigured, but disabled by default.

To enable GA support:

1. Define your GA ID and other `vue-analytics` settings in `config.analytics.js`
2. Uncomment the line in `@vendor/vue.js` where `vue-analytics` is `imported`

## Other analytics providers

To configure any other analytics solution, initialise its JS SDK in a new file under `src/vendor/` and import this file in `main.js`.
