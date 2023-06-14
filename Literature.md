---
type: paper
aliases:
- "{{title}}"
- {{citekey}}
- "{{shortTitle}}"
url: {{url}}
doi: {{doi}}
tags: 
{%- for tag in tags %}
- {{tag.tag | replace("-", "/") | replace (" ", "_") | replace ("_/_", "/")}}
{%- endfor %}
citekey: {{citekey}}
keywords: {{allTags}}
authors: [{{authors}},{{directors}}]
status: Planned
---

<%*
	// Templater function to rename the file after importing it.
	let title = "{{title}}";
	title = title.replace(/[/\\?%*:|"<>]/g, '-');
	let date = tp.date.now("YYYY-MM-DD");
	await tp.file.rename(`& ${date} ${title}`);
_%>

zotero_link::{{pdfZoteroLink}}
abstract::{{abstractNote}}
{% for relation in relations -%}
{%- if relation.citekey -%}
	related::[[{{relation.citekey}}|{{relation.citekey}}]]
{% endif -%}
{%- endfor %}

```dataview
TABLE keywords as Keywords, type as Type, related as Related
FROM [[& <%tp.date.now("YYYY-MM-DD")%> {{title}}]]
WHERE related != null
```
# Hypothesis
- 

# Methodology
- 

# Results
- 

# Key Points
- 

# Notes

|Highlighted Color| Meaning|
|-|-|
|<mark style="background: #ADCCFFA6;">Blue</mark>|Key Points|
|<mark style="background: #FF5582A6;">Red</mark>|Disagree with Author|
|<mark style="background: #FFB86CA6;">Orange</mark>|Interesting Statement by Author|
|<mark style="background: #BBFABBA6;">Green</mark>|Interesting Point (General)|
|<mark style="background: #FFF3A3A6;">Yellow</mark>|Interesting Mathematical Concept|
|<mark style="background: #D2B3FFA6;">Purple</mark>|Interesting Reference|

{% for annotation in annotations -%}
	{%- if annotation.annotatedText -%}
	 <mark class="hltr-{{annotation.colorCategory | lower }}">"{{annotation.annotatedText}}"</mark> [Page {{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}&annotation={{annotation.id}})
	{%- endif %}
	{%- if annotation.imageRelativePath -%} ![[{{annotation.imageRelativePath}}]]	[Page {{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}&annotation={{annotation.id}})
	{%- endif %}
{% if annotation.comment %}
- {{annotation.comment}}
{% endif %}
{% endfor -%}
# Related Concepts
_Hashtags and links to other files_ 

___
Last modified: `=this.file.mtime`