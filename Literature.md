---
type: paper
aliases:
- {{title}}
- {{citekey}}
url: {{url}}
doi: {{doi}}
citekey: {{citekey}}
keywords: {{allTags}}
authors: [{{authors}},{{directors}}]
status: Planned
created:
updated:
---

<%*
	// Templater function to rename the file after importing it.
	let title = "{{title}}";
	let date = tp.date.now("YYYY-MM-DD");
	await tp.file.rename(`& ${date} ${title}`);
_%>

zotero_link::{{pdfZoteroLink}}
abstract::{{abstractNote}}
{% for relation in relations -%}
{%- if relation.citekey -%}
	related::{{relation.citekey}}
{% endif -%}
{%- endfor %}

```dataview
TABLE created, updated as modified, tags, type, related
FROM [[& <%tp.date.now("YYYY-MM-DD")%> {{title}}]]
WHERE related != null
```


# Key Findings

# Relevant Quotes

# Impressions

# Related Concepts
_Hashtags and links to other files_ 

___
Last modified: `=this.file.mtime`