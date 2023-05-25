---
type: daily
tags: 
  - todo
date: {{date}}
aliases: 
- {{date:DD.MM}}
- {{date:dd DD.MM}}
- {{date:DD.MM.YYYY}}
---
# Daily Information:
- Week: {{date:wo}} of 52nd
- Started: {{time}}
- Home Office: ✔️❌

# To-Do
- 

# Miscellaneous Notes
- 

# Pending Tasks:
```dataview
task
FROM #todo 
Where !completed and
	type != "workpackage"
	and date(due) <= date(this.file.ctime)
Sort due
GROUP BY file.link
```
# Near Future Tasks':
```dataview
Table due as Deadline, remaining as Remaining, status as Status
FROM #todo 
Where !completed and
	type != "workpackage"
	and date(due) > date(this.file.ctime)
SORT due
```

___
Note Last Modified: `=this.file.mtime`