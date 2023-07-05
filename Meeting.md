---
type: Meeting
tags: 
project: 
place:
duration:
date: {{date:YYYY-MM-DD}}
participants:
- John Doe
aliases:
- Meeting {{date:DD.MM}}
- Meeting {{date:dd DD.MM}}
- Meeting {{date:DD.MM.YYYY}}
recorder: "John Doe"
protocol_ctime: {{date}}
created: 
updated: 
---
|Date|`=this.date`|
|-|-|
|Project|`=this.project`|
|Meeting Place|`=this.place`|
|Participants|`=this.participants`|
|Recorder|`=this.recorder`|
|Protocol created on|`=this.protocol_ctime`|


# Agenda
1. 

# Action Items
- 

# Discussion Points
- 

# Requires Query
```dataview
List
WHERE project = this.project and
	type = "workpackage" and
	status = "RequiresQuery"
```

# Decisions Made
- 

# Next Steps
- [ ] 

___
Last Modified `=this.updated`
