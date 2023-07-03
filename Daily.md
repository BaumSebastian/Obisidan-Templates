---
type: daily
tags: 
  - todo
aliases: 
- {{date:DD.MM}}
- {{date:dd DD.MM}}
- {{date:DD.MM.YYYY}}
created: 
updated: 
doy: {{date:DDD}}
woy: {{date:ww}}
---
# Year Overview
`$= const value=dv.current().doy; const max = 365;"<progress value='" + value + "' max='" + max + "'></progress>" + "<span style='font-size:smaller;color:var()'>" + Math.round(100.0*value/max,2) + "%&nbsp;| &nbsp;" + parseInt(max - value) +  " days left | Week [" + dv.current().woy + "/52]</span>"`

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
# Links
- [[<%tp.date.now("YYYY-MM-DD", -1)%>|Yesterdays Daily Note]]
- [[<%tp.date.now("YYYY-MM-DD", +1)%>|Tomorrows Daily Note]]
