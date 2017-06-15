
# IDE integration

All pipeline configuration (linters etc.) can be consumed by plugins of any editor.

## Visual Studio Code

Workspace configuration is included in the project. The configuration instructs VS Code about certain file location, how to treat certain file extensions, and configure some commonly used extensions to work with the project, including single-file `.vue` components.

```
.vscode/
    |_ settings.json
```

Installing the following extensions for VS Code will make your life easier:

- [EditorConfig for VS Code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig) adds support for `.editorconfig` auto formatting rules.
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) integrate JavaScript linting direclty in the editor.
- [Stylelint](https://marketplace.visualstudio.com/items?itemName=shinnn.stylelint) integrate (S)CSS linting directly in the editor.
- [TODO Highlight](https://marketplace.visualstudio.com/items?itemName=wayou.vscode-todo-highlight) highlights TODO, FIXME and other similar comments in the editor.
- [Version Lens](https://marketplace.visualstudio.com/items?itemName=pflannery.vscode-versionlens) visualizes the installed versions of packages and easily update versions when editing `package.json`.
- [vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur) supports common editor features in single-file components better (since `.vue` files use several different languages).

There are many other good extensions in the Marketplace as well. Extensions can be installed directly from the editor.

VS Code will show linting issues inline while editing, and also as a list in the _problems_ toolbar.
