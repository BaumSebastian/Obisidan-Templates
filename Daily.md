---
type: daily
tags:
aliases: 
- <%tp.date.now("DD.MM")%>
- <%tp.date.now("dd DD.MM")%>
- <%tp.date.now("DD.MM.YYYY")%>
created: 
updated: 
doy: <%tp.date.now("DDD")%>
woy: <%tp.date.now("ww")%>
---
# Year Overview
```dataviewjs
const value = dv.current().doy;
const max = 365;

dv.paragraph("<progress value='" + value + "' max='" + max + "'></progress>" + "<span style='font-size:smaller;color:var()'>" + Math.round(100.0*value/max,2) + "%&nbsp;| &nbsp;" + parseInt(max - value) +  " days left | Week [" + dv.current().woy + "/52]</span>")
```

# Daily Tasks
### Morning Tasks
- [ ] 

### Afternoon Tasks
- [ ] Check Emails 🛫 <%tp.date.now("YYYY-MM-DD")%> 📅 <%tp.date.now("YYYY-MM-DD")%> ⏰<%tp.date.now("YYYY-MM-DD")%> 15:00 🔽 

### General Tasks
- [ ] 

```dataviewjs
let moc_pages = dv.pages().where(p => p.type == "moc").file.link;

if (moc_pages.length > 0){
	dv.header(1, "MOC Overview");
	dv.list(moc_pages)
}
```
```dataviewjs
let po_pages = dv.pages().where(p => p.type == "project_overview" && p.project).file.link;

if (po_pages.length > 0){
	dv.header(1, "Project Overview");
	dv.list(po_pages)
}
```
# Task Overview
```dataviewjs
const today = '<%tp.date.now("YYYY-MM-DD")%>'
const exclude_path = "00 Obsidian Organisation" 
const thisDay = dv.date(today).day

// Get all non-completed task, just one time
const alltasks = dv.pages('-"' + exclude_path + '"')
  .where(p => p.type != "workpackage")
  .file.tasks
  .where(t => !t.completed && t.text)

// My wanted tasklists
let overdueTasks = []
let dueTasks = []
let startingTasks = []
let ongoingTasks = []
let noDateTasks = []

// Loop through all tasks _once_, and filter them
for (let task of alltasks) {
	if (task.due && task.due.day < thisDay) 
	    overdueTasks.push(task)
	if (task.due && task.due.day == thisDay)
	    dueTasks.push(task)
    if (task.start && task.start.day == thisDay)
	    startingTasks.push(task)
	if (task.start && task.start.day < thisDay) 
	    ongoingTasks.push(task)
	if (!task.start)
		noDateTasks.push(task)
}
// Display the various taskslist, _if_ they
// have any tasks at all

if (overdueTasks.length > 0) {
  dv.header(3, "<u>Overdue⚠️</u>");
  dv.taskList(overdueTasks, true);
}  

if(dueTasks.length > 0) {
  dv.header(3, "<u>Due today⏰</u>");
  dv.taskList(dueTasks, false);
}  

if (startingTasks.length > 0) {
  dv.header(3, "<u>Starting today🌅</u>");
  dv.taskList(startingTasks, false);
}  

if (ongoingTasks.length > 0) {
  dv.header(3, "<u>Ongoing tasks🚀</u>");
  dv.taskList(ongoingTasks, false);
}

if (noDateTasks.length > 0){
	dv.header(3, "<u>No Start Date assigned⚪️</u>")
	dv.taskList(noDateTasks, false);
}
```
# Links
[[<%tp.date.now("YYYY-MM-DD", -1)%>|Previous Note]] <-> [[<%tp.date.now("YYYY-MM-DD", +1)%>|Next Note]]

___
Last Modified `=this.updated`
