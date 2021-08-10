# The reason that why use arvisworkflow.json instead of info.plist of alfred workflow

info.plist is config file of alfred workflow.

I made a converter info.plist to alfredworkflow.json.

1. `info.plist` is not human-readable. `info.plist` have kind of DAG (directed acyclic graph), this make very difficult to read `info.plist`. So I decided to make json format replacing the info.plist. I replaced the DAG structure with simple json tree made up of `trigger` and `action`, and removed each node's position infomation.

2. `info.plist` belongs to alfred. it can be updated anytime, I think using this in Arvis is not reasonable.
