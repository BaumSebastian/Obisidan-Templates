---
project:
tags:
---

# General Information
```dataviewjs
// variables

let status = {
	"Done":"🟢",
	"Cancelled":"🔴", 
	"InProgress":"🔵",
	"Planned":"🟡",
	"Blocked":"🟠",
	"Dormant":"🟤",
	"External": "⚪",
	"RequiresQuery": "❓"}

// Get all workpackages
let wps = dv.pages().where( p=>
	// Check if the pages has metadata 'project' and is from the same project
	p.project && p.project == dv.current().project &&
	// Check if it is a workpackage Overview
	p.type && p.type == "workpackage"
	);

let wp_all = wps.length

if (wp_all > 0){
	dv.header(2, "Work packages status (total: "+wp_all+"):");
	for(let key in status){
		let wp_status = wps.where(wp => wp.status == key).length
		dv.paragraph("Work packages " + key + status[key]+ ": " + wp_status + "/" +wp_all + " (" + Number(((wp_status /wp_all)*100).toFixed(1)) + "%)")
		}
}
else {
dv.paragraph("No information to display")
}
```

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

