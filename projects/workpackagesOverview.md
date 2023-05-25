---
project:
tags:
start:
due:
status:
type: workpackageOverview
workpackage_identifier: 
---

# Content
_content of these work packages?_

## Work packages
```dataview
TABLE status as Status, supervisor as Supervisor, start as Start, due as Deadline
WHERE contains(file.name, this.workpackage_identifier) and 
	project = this.project and
	type = "workpackage" 
SORT file.name
```

# Deliverables
```dataview
TASK
WHERE contains(file.name, this.workpackage_identifier) and 
	project = this.project and
	type = "workpackage" 
SORT file.name 
GROUP BY file.link
```

___
Last modified: `=this.file.mtime`