---
project:
description:
type: workpackageOverview
tags:
start:
due:
status:
group:
workpackage_identifier: 
---

# Content
_content of these work packages?_

# Progress
```dataviewjs
const this_project = dv.current().project;
const observed_status = ["Done","InProgress","Planned","RequiresQuery", "Blocked", "External"]
const status_emoji = {
	"Done" : "🟢",
	"InProgress" : "🔵",
	"Planned" : "🟡",
	"RequiresQuery" : "❔",
	"Blocked" : "🟤",
	"External" : "⚪"
}

let aps = dv.pages().where(p => p.project == this_project 
	&& p.group == dv.current().group
	&& p.type == "workpackage"
	&& p.status != "")

// All arrays of interesting
const max = aps.length

for (let status of observed_status){
	let amount_status = aps.where(ap => ap.status == status).length
	dv.paragraph(status_emoji[status]+insertSpacesBeforeUppercase(status))
	dv.paragraph(progressBarVisualization(amount_status, max))
}

function insertSpacesBeforeUppercase(inputString) {
  return inputString.replace(/([A-Z])/g, ' $1');
}

function progressBarVisualization(value, max){
	const percentage = ((value/max)*100).toFixed(1);
	return "<progress value='" + value + "' max='" + max + "' style='color: blue;'></progress><span style='font-size: smaller'> " + percentage + "% | [" + value + "/" + max + "]</span>";

}
```

# Work packages
```dataviewjs
const ignoring_workpackages = []
const current_project = dv.current().project
let pages = dv.pages().where(p => p.project == current_project
								&& p.group == dv.current().group
								&& p.type == "workpackage"
								&& !ignoring_workpackages.includes(p.status))

for( let page of pages){
	dv.header(3, page.file.link)
	dv.paragraph("Deadline: " + page.due)
	if (page.file.tasks.length > 0)
		dv.taskList(page.file.tasks.groupBy(p => p="Deliverables:"))
}
```

___
Last modified: `=this.file.mtime`