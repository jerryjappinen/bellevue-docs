# App meta data

All meta data of your application comes from the [centralised configuration](../app/config.md).

## Site-wide meta tags

This project comes with extensive templating for printing meta tags based on the [centralised configuration](https://github.com/Eiskis/bellevue/tree/master/src/config/config.base.js). Most common use cases, such as `viewport` definitions for mobile browsers, are editable in the config file and you don't have to worry about writing the exact and sometimes obscure HTML code. For a quick overview of the tags that are be printed, check out the [ugly source code for `index.html.ejs`](https://github.com/Eiskis/bellevue/tree/master/src/index.html.ejs).

If you really want to add custom meta tags or similar code to your site, you can edit `index.html.ejs` in any way you please. If you find yourself manually adding tags for a common use case, consider [filing an issue or PR](https://github.com/Eiskis/bellevue/issues) so that the tags can be included in Bellevue.

## Page-specific meta tags

Use the `metaInfo` property in your page component.The `vue-meta` plugin is included in this template and it can control the page title and other tags depending on which components are rendered.

- [Read more about creating routed pages](../ui/routing.md)
- [Read more about `vue-meta`](https://github.com/declandewet/vue-meta)

## Web app manifest

- [`config/meta.json`](https://github.com/Eiskis/bellevue/tree/master/src/config/meta.js)
- [`config/tooling/manifest.json`](https://github.com/Eiskis/bellevue/tree/master/src/config/tooling/manifest.js)

## Robots

You can control your robot meta tags and `robots.txt` easily with [`config/meta.json`](https://github.com/Eiskis/bellevue/tree/master/src/config/meta.js) and [`config/tooling/robots.json`](https://github.com/Eiskis/bellevue/tree/master/src/config/tooling/robots.js).

## Sitemap

A `sitemap.xml` is automatically generated for your app based on your routes. If you want more control over how the sitemap should look like, see [`config/tooling/sitemap.json`](https://github.com/Eiskis/bellevue/tree/master/src/config/tooling/sitemap.js)
