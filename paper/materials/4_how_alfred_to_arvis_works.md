# How alfred-to-arvis works

1. Read `info.plist` and iterate all node, find trigger node (which means input type is hotkey or keyword or scriptfilter.)

2. Repeat finding next nodes starting with the trigger node recursively.

3. If next node is not supported, stop iterating, find another next node.

4. If next node is supported, extract the node's information.

5. Write extracted information to `arvisworkflow.json`