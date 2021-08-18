# About module structure

arvis are built with `electron-react-boilerplate`.

So, basic project structure and webpack, babel setting files are same with `electron-react-boilerplate`.

## Two package.json structure

* `./src/package.json` relative to the project root

: native modules shoulde be specified in here.

For example, `iohook`, `fsevents`, `robotjs` are specified in here because they are native modules which means they are builded according to the platform at build time.

* `./package.json` in the root of your project

: All module except for native modules are specified in here.

## External modules

External modules are `src/external`.

There are folling source codes.

* Type declarations of typeless modules (easy-auto-launch)

* Some css files for updating module's style (react-tabs, react-prosidebar, github-markdown-css, jsoneditor)

* Some library with extended functionality (use-key-capture)

* Some library with no webpack-bundling (about-window)
