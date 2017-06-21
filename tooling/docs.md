
# Generating docs

There is a preconfigured way of generating code docs with [Docco](https://jashkenas.github.io/docco/). It isn't a very sophisticated tool, but it can be used to auto generate readable docs from code comments.

To generate docs, use one of these `npm` scripts on the command line:

```sh
# All docs
npm run docs

# Docs for individual JS code dirs
npm run docs:components
npm run docs:directives
npm run docs:mixins
npm run docs:models
npm run docs:plugins
npm run docs:services
npm run docs:util

# Global styles
npm run docs:styles
```

**Known issue:** Docco does not generate menus or index pages, only the HTML files corresponding to each source file.

**Note:** you can change the output directory, but you will have to do so by updating these scripts in `package.json`. This way you can keep the generated docs in a separate repository, for example.

**Note:** docs are currently ignored in Git. If you wish to store docs in your repository, remove `docs/.gitignore`.
