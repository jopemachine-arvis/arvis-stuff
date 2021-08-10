# About arvis-extension-validator

arvis-extension-validator includes json-schema for validating arvis-extension,

and also include library for validating.

Arvis use this library when install new extension to filter not valid extensions which can break arvis's behavior.

Extension developers also can use arvis-extension-validator cli tool for validating for their extension.

(This cli tool is also included in arvish)

And by including this library's json schema in their extension json file,

vscode automatically check the extension json file is valid.

`arvish init` command and `generator-arvis` make skeleton extension json file including this library's schema.