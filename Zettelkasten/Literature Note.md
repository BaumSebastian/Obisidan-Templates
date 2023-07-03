---
id: "0001" # For sequence structure of the atomic notes to itself
aliases:
- {{title}}
tags: # For realted concepts 
  -
zn_type: literature
# Both meta data below is for the "Update time on edit" plugin
created: 
updated: 
---

<%*
	// Templater function to rename the file after importing it.
	let title = tp.file.title;
	let id = tp.frontmatter.id;
	let date = tp.date.now("YYYY-MM-DD");
	await tp.file.rename(`${date} ${id} ${title}`);
_%>

# {{title}}
_There should be a 'Body' for the note - where the main content goes. Inside the body one may want to link to other content - like you see in Wikipedia._

# References
_To outside source material - if the note is a summary of other content it should reference it such as for your citations._

___
Last Updated `=this.updated`