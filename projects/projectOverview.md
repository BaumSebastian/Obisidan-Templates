---
type: project_overview
project:
tags:
---

# Content
_Content of this project_

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

# Meetings
```dataviewjs
let meeting_pages = dv.pages().where(p => p.project == dv.current().project && p.type == "Meeting")

if (meeting_pages.length > 0){
	dv.table(["File", "Date", "Place"],
		meeting_pages
		.sort(p => p.date)
		.map(p => [p.file.link,
			p.date,
			p.place, 
		]) 
	)
}
else {
dv.paragraph("No meetings so far.")
}
```

```dataviewjs
let project_pages = dv.pages().where(p => p.project == dv.current().project).sort(p => p.file.name) 

// Check if overview exists
let overview_pages = project_pages.where(p => p.type== "workpackageOverview")
if (overview_pages.length > 0){
	dv.header(1,"Groups")
	for (let page of overview_pages){
		dv.paragraph(page.file.link + " - " + page.description)
	}
}
else {
	dv.header(1,"Work Packages")
	for (let page of project_pages){
		dv.paragraph(page.file.link + " - " + page.description)
	}
}
```
___
Last modified: `=this.file.mtime`