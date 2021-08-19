# How workflow feature works

## How workflow's actions are executed

workflow config (arvis-workflow.json) are loaded when arvis starts up in memory.

and whenever user input changes arvis finds commands from there.

when user press enter on a result, the command's 'action' is executed.

## How workflow's scripts are executed

workflow's source files are not loaded in arvis.

only arvis-workflow.json file's information are loaded in arvis at startup.

This file indicate which commands are available in the workflow, and some source code file the command need to.

When the command are executed, specified source file are executed as child process through `execa`.

The child process inherit the user's shell's environment variables like `PATH`,

`variables` specified by extension developer's.

When the child process ends, child process's execution result are forwarded to arvis as form of Promise.

And the promise returns `stdout`, `stderr` of the child process.

So, arvis can notify users the result of the script in their search window.
