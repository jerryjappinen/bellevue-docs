
# Setting page meta information

**How do I control page title and meta tags in the single-page applicatiom?**

## Auto-injected meta tags

Some Webpack plugins print the meta tags needed for the functionality they want to deliver. For example, there is a plugin that resizes app icons and also generates the meta tags required by iOS to use them.

## Site-wide meta tags

This project comes with extensive templating for printing meta tags based on the [centralised configuration](https://github.com/Eiskis/bellevue/tree/master/src/config/config-base.js). Most common use cases, such as `viewport` definitions for mobile browsers, are editable in the config file and you don't have to worry about writing the exact and sometimes obscure HTML code. For a quick overview of the tags that are be printed, check out the [ugly source code for `index.html.ejs`](https://github.com/Eiskis/bellevue/tree/master/src/index.html.ejs).

If you really want to add custom meta tags or similar code to your site, you can edit `index.html.ejs` in any way you please. If you find yourself manually adding tags for a common use case, consider [filing an issue or PR](https://github.com/Eiskis/bellevue/issues) so that the tags can be included in Bellevue.

## Page-specific meta tags

Use the `metaInfo` property in your page component.The `vue-meta` plugin is included in this template and it can control the page title and other tags depending on which components are rendered.

- [Read more about creating routed pages](../ui/routing.md)
- [Read more about `vue-meta`](https://github.com/declandewet/vue-meta)
