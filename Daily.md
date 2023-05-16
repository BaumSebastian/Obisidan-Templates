---
category: [note, daily, todo]
type: daily
tags: todo
date: {{date}}
aliases: [{{date:DD.MM}}, {{date:dd DD.MM}}, {{date:DD.MM.YYYY}}]
---
# Daily Information:
- Week: {{date:wo}} of 52nd
- Working Time: {{time}} - 17:30
- Home Office: ✔️❌

# To Do:
```dataview
TASK
From #todo
WHERE !completed 
GROUP BY file.link
```

# General topics
- 

# Open Topics
Topics that are a unchecked task and not marked as completed.
```dataview
TASK 
FROM -#todo
WHERE !completed 
GROUP BY file.link
```

___
Note Last Modified: `=this.file.mtime`