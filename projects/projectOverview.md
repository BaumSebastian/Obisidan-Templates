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
	p.project == dv.current().project &&
	// Check if it is a workpackage Overview
	p.type && p.type == "workpackage"
	);

let wp_all = wps.length

if (wp_all > 0){
	dv.header(2, "Work packages status (total: "+wp_all+"):");
	for(let key in status){
		let wp_status = wps.where(wp => wp.status == key).length
		dv.paragraph(key + status[key]+ ": " + wp_status + "/" +wp_all + " (" + Number(((wp_status /wp_all)*100).toFixed(1)) + "%)")
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

// functions to show tasks under section names
function showTasksGroupedBySection(page) {
    let all_tasks = page.file.tasks
    if (all_tasks.length == 0)
    {
        return
    }

    for (let group of all_tasks.groupBy(t => t.section)) {
        dv.header(4, group.key)
        dv.taskList(group.rows, false)
    }
}



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

// Check if overviews are added
let show_overviews = workpackageOverviews.length > 0
let displaying_packages = workpackages

if (show_overviews) {
	displaying_packages = workpackageOverviews;
}

for (let pkg of displaying_packages){
	// Get additional header info
	let desc = ""
	if (pkg.description) {
		desc = " - " + pkg.description
	}
	dv.header(2, pkg.file.link + desc);
	
	// Display tasks
	if (show_overviews)
	{
		showTasksGroupedBySection(workpackages.where(wp => wp.file.name.includes(pkg.workpackage_identifier)));
	} else {
		showTasksGroupedBySection(pkg);
	}
}
```

