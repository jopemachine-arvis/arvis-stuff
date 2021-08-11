# How workflow feature works

## How workflow scripts are executed

workflow's source files are not loaded in arvis.

only arvis-workflow.json file's information are loaded in arvis at startup.

This file indicate which commands are available in the workflow, and some source code file the command need to.

When the command are executed, specified source file are executed as child process through `execa`.

The child process inherit the user's shell's environment variables like `PATH`,

`variables` specified by extension developer's.

When the child process ends, child process's execution result are forwarded to arvis as form of Promise.

And the promise returns `stdout`, `stderr` of the child process.

So, arvis can notify users the result of the script in their search window.

## How workflow's actions are parsed

