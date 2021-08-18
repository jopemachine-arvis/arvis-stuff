# About file watching (chokidar)

arvis use chokidar to keep watch file change event.

File watching is using on `extension changes`.

For example, new arvis-workflow.json file is created on extensions folder, arvis detect it, trigger extension-reload function.

By doing this, after install new extension, arvis can reload its extensions.

On workflow extension folders, chokidar only watchs arvis-workflow.json because other files are not loaded in arvis.

(Other files are used through inter process communication.)

But on plugin extension folder, chokidar watchs extension root folder's javascript files, because they are all loaded in arvis.

The reason chokidar doesn't watch all javascript file is that to reduce system resource consume.

chokidar's file watching can use lots of system resources if chokidar should watch all files in extension folders.

arvis use chokidar to keep watch file change event.

File watching is using on `extension changes`.

For example, new arvis-workflow.json file is created on extensions folder, arvis detect it, trigger extension-reload function.

By doing this, after install new extension, arvis can reload its extensions.

On workflow extension folders, chokidar only watchs arvis-workflow.json because other files are not loaded in arvis.

(Other files are used through inter process communication.)

But on plugin extension folder, chokidar watchs extension root folder's javascript files, because they are all loaded in arvis.

The reason chokidar doesn't watch all javascript file is that to reduce system resource consume.

chokidar's file watching can use lots of system resources if chokidar should watch all files in extension folders.

Ideally, chokidar should watch all javascript file of custom plugin to support hotload, I think reducing system resources is more important than hotload support,

So I restricted monitoring to root folder's js files (and arvis-plugin.json file) only.
