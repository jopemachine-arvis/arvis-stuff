# How arvis-store works

arvis-store works as `Github as a backend`.

Which means all datas used in arvis-store are stored in Github, and these datas are updated through github action.

This github action for updating store is triggered twice a day automatically.

When the action is triggered, internal/store.json file is updated.

This file store each extension's weekly, total download count, name, latest version.

By doing this update, each extension's info can be kept up to date.

To add new extension to arvis-store, extension developer need to register their github authentification token to arvis-store cli tool.

With this token, arvis-store cli tool make a PR adding the extension info to internal/static-store.json.

static-store.json stores the extension's static information like name, creator, description, homepage.

This information usually needs not be updated.

(If they need to the renewal of extension info, they can simply create a PR editing the static info.)

And arvis-store provides some simple API allowing users get extension info.

arvis use this API for providing store feature in arvis GUI application.

There are some types that extension developer can upload.

This type are specified when extension developer uploaded their extension.

This type decide the user install the extension. 

* npm: Install the extension from npm.

* local: Download the extension data as base64 format from arvis-store and install that by local.