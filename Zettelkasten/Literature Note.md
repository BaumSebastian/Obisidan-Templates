---
id: '<%tp.date.now("YYYY-MM-DD-HH-mm")%>'
aliases:
- {{title}}
tags: # For realted concepts 
  -
zn_type: literature
# Both meta data below is for the "Update time on edit" plugin
created: 
updated: 
version: draft
comment: "If you want to write something about this note"
description: "One Sentence to explain the note"
---

<%*
	// Templater function to rename the file after importing it.
	let title = tp.file.title;
	await tp.file.rename(`${tp.date.now("YYYY-MM-DD-HH-mm")} ${title}`);
_%>


# {{title}}
_There should be a 'Body' for the note - where the main content goes. Inside the body one may want to link to other content - like you see in Wikipedia._

# References
_To outside source material - if the note is a summary of other content it should reference it such as for your citations._

___
Last Modified `=this.updated`