# Localisation

Localisation is **not** preconfigured, but can be added easily.

To enable localisation, we recommend [`vue-i18n`](http://kazupon.github.io/vue-i18n/en/). This plugin supports localised copy text, date formatting, number formatting and crude pluralisation. It also offers a nice set of various ways to organise the localisation depending on your needs.

More plugin options are listed on [Awesome Vue.js](https://github.com/vuejs/awesome-vue#i18n).

## Adding `vue-i18n` support

Localisation is fairly easy to add.

1. Add localisation files under `src/locales/`
2. Add an alias `'@locales': 'src/locales'` in `src/config/tooling/config.aliases.js`
3. `install vue-i18n --save`
4. Load and configure `vue-i18n` [as a plugin](../faq/vue-plugins)

You can now use localisation in your `.vue` components as described in the [documentation](http://kazupon.github.io/vue-i18n/en/started.html).
