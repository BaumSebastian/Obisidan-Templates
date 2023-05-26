---
project:
tags:
---
# Meetings
```dataview
TABLE date, duration, place
WHERE type = "Meeting" and project = this.project
SORT date
```

# Work packages
_Displays all work packages of the project_
```dataview
TABLE status as Status, start as Start, due as Deadline, dependencies as Dependencies, supervisor as Supervisor
WHERE type = "workpackage" and
	project = this.project
SORT file.name
```
# Work package overviews
_References the work package overviews_
```dataviewjs
// variables
let content_headline = "Content"
let deliverables_headline = "Deliverables"

// Get all pages related to this project
let projectpages = dv.pages().where( p =>
	// Check if the pages has metadata 'project'
	p.project && 
	// Check if the page is from the same project
	p.project == dv.current().project
	);

// Get all workpackage overviews
let workpackageOverviews = projectpages.where( p =>
	// Check if it is a workpackage Overview
	p.type && p.type == "workpackageOverview");

// Get all workpackages
let workpackages = projectpages.where( p=>
	// Check if it is a workpackage Overview
	p.type && p.type == "workpackage");

for (let wO of workpackageOverviews){
	// Get additional header info
	let desc = ""
	if (wO.description) {
		desc = " - " + wO.description
	}
	
	// Heading
	dv.header(2, wO.file.link + desc);
	
	// Deliverables of the workpackage
	dv.header(3, deliverables_headline + ":");
	dv.taskList(workpackages.where(wp => wp.file.name.includes(wO.workpackage_identifier)).file.tasks, false);
}
```

