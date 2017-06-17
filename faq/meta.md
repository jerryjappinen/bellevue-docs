
# Setting page meta information

**How do I control page title and meta tags in the single-page applicatiom?**

## Template meta tags

Some Webpack plugins print the meta tags needed for the functionality they want to deliver. For example, there is a plugin that resizes app icons and also generates the meta tags required by iOS to use them.

However you are free to add any other meta tags to `index.html.ejs`. These are typically not dynamic, but variables can be passed from Webpack config to the EJS template for printing during compilation.

## Page-specific meta tags

Use the `metaInfo` property in your page component.The `vue-meta` plugin is included in this template and it can control the page title and other tags depending on which components are rendered.

- [Read more about creating routed pages](../ui/routing.md)
- [Read more about `vue-meta`](https://github.com/declandewet/vue-meta)
