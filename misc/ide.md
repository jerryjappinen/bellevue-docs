
# IDE integration

Linting and other parts of the tooling can be integrated to most common editors. Each editor generally has extensions that will read the same configuration that the Webpack and command line tools use, so you will get an IDE experience that's consistent with the other tools.

## Visual Studio Code

Workspace configuration is included in the project. The configuration instructs VS Code about certain file location, how to treat certain file extensions, and configure some commonly used extensions to work with the project, including single-file `.vue` components.

```
.vscode/
	└── settings.json
```

Installing the following extensions for VS Code will make your life easier:

|Extension|Description
|---|---
|[EditorConfig for VS Code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)|Adds support for `.editorconfig` auto formatting rules.
|[ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)|Integrate JavaScript linting direclty in the editor.
|[npm](https://marketplace.visualstudio.com/items?itemName=eg2.vscode-npm-script)|Adds support for running npm scripts and validating the installed modules against `package.json`.
|[npm IntelliSense](https://marketplace.visualstudio.com/items?itemName=eg2.vscode-npm-script)|Autocompletes npm modules in import statements.
|[Stylelint](https://marketplace.visualstudio.com/items?itemName=shinnn.stylelint)|Integrate (S)CSS linting directly in the editor.
|[TODO Highlight](https://marketplace.visualstudio.com/items?itemName=wayou.vscode-todo-highlight)|Highlights TODO, FIXME and other similar comments in the editor.
|[Version Lens](https://marketplace.visualstudio.com/items?itemName=pflannery.vscode-versionlens)|Visualizes the installed versions of packages and easily update versions when editing `package.json`.
|[vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur)|Supports common editor features in single-file components better (since `.vue` files use several different languages).

There are many other good extensions in the Marketplace as well. Extensions can be installed directly from the editor.

VS Code will show linting issues inline while editing, and also as a list in the _problems_ toolbar.
