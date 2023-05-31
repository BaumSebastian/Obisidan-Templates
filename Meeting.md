---
type: Meeting
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
---
|Date|`=this.date`|
|-|-|
|Project|`=this.project`|
|Meeting Place|`=this.place`|
|Participants|`=this.participants`|
|Recorder|`=this.recorder`|
|Protocol created on|`=this.protocol_ctime`|

<%*
	// Templater function to rename the file after importing it.
	let date = tp.date.now("YYYY-MM-DD");

	// Check if this Meeting is assigned to an project
	if tp.file.content.
	await tp.file.rename(`${date}-${title}`);
_%>

# Agenda
1. 

# Action Items
- 

# Discussion Points
- 

# Decisions Made
- 

# Next Steps
- 

___
Last modified: `=this.file.mtime`
