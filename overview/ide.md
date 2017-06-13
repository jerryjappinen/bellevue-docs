
# IDE integration

All pipeline configuration (linters etc.) can be consumed by plugins of any editor.

## Visual Studio Code

Workspace configuration is included in the project. The configuration instructs VS Code about certain file location, how to treat certain file extensions, and configure some commonly used extensions to work with the project, including single-file `.vue` components.

```
.vscode/
    |_ settings.json
```

Installing the following extensions for VS Code will make your life easier:

- `EditorConfig for VS Code`: support for `.editorconfig` auto formatting rules.
- `ESLint`: Integrate JavaScript linting in the editor.
- `stylelint`: Integrate (S)CSS linting in the editor.
- `TODO Highlight`: Highlight TODO, FIXME and other similar comments in the editor.
- `Version Lens`: Visualize the installed versions of packages and easily update versions when editing `package.json`.
- `vetur`: Support common editor features in single-file components better (since `.vue` files use several different languages).

VS Code will show linting issues inline while editing, and also as a list in the _problems_ toolbar. There are many other good extensions in the Marketplace as well.
