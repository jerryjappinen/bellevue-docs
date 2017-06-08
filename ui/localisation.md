
# Localisation

Localisation capability is included in the template and is handled with [`vue-i18n`](http://kazupon.github.io/vue-i18n/en/).

This plugin supports localised copy text, date formatting, number formatting and crude pluralisation. It also offers a nice set of various ways to organise the localisation depending on your needs.

## Aspects of localisation

- Localised copy text
- Date and time formatting
- Number formatting

## Removing localisation support

If you don't need localisation, it might be better to just get rid of the complexity of `vue-i18n`. It's also fairly easy to add back in later if you need it in the future.

1. Remove dependency: `vue-i18n` from `package.json`
2. Remove or comment the parts in `src/vue/plugins/index.js` where `VueI18n` is imported and exported.
3. Remove or comment the part in `src/main.js` where `plugins.VueI18n` is passed to Vue.
4. Remove `src/vue/plugins/vue-i18n.js`.
5. Clean up sample code that uses localisation
	- In the script part of `.vue` components: `this.$t()` or `this.$d()`
	- In the template part of `.vue` components: `$t()` or `$d()`
