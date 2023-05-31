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

# Daily Tasks
- 

# From Previous Notes
```dataview
task
FROM #todo 
Where !completed and
	type != "workpackage"
	and date(due) <= date(this.file.ctime)
Sort due
GROUP BY file.link
```

# Miscellaneous Notes
- 

# Pending Tasks:
```dataview
Table due as Deadline, priority as Priority, overdue as Overdue, status as Status
FROM #todo
Where status != "Done" and
	type != "workpackage" and
	type != "daily" and
	date(due) <= date(this.file.ctime)
FLATTEN date(today) - date(due) as overdue
SORT overdue and priority
````
# Upcoming Tasks:
```dataview
Table due as Deadline, priority as Priority, remaining as Expiring, status as Status
FROM #todo 
Where status != "Done" and
	type != "workpackage"
	and date(due) > date(this.file.ctime)
FLATTEN date(due) - date(today) as remaining
SORT remaining and priority
````

___
Last Modified: `=this.file.mtime`