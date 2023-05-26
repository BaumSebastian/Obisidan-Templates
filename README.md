![banner](obsidian_banner.png)
# Obsidian Templates
This repository contains templates for Obsidian notes.
- Why Obsidian: Watch following from [linking your thinking](https://www.youtube.com/@linkingyourthinking/featured):
  ![Video](https://www.youtube.com/watch?v=QgbLb6QCK88)
- Why Templates: Speed up your process when working with obsidian.

# How to use these Templates
To use this templates:
1. Download and install [Obsidian](https://obsidian.md/download).
2. Create a vault and inside your vault a folder for templates location like following example:
  ```
  my_vault/
	  > templates
  ```
1. Set the new folder `my_vault/templates` as default folder for templates in: `settings` > (core plugins) `templates` > `template folder location`.
2. Clone this repository inside of your `my_vault/templates` folder
3. Create a new note (`ctrl+n`)
4. Press `ctrl+p` and search for `templates: insert template`
5. Insert the template!
Some templates (like [Daily Note template](##Daily)) require additional settings. This is indicated by a "Setup" section in the template.

# Plugins
There is a whole bunch of community plugins available. I highly recommend using them, as they will speed up your Obsidian-workflow. The plugins I use for these templates are:
- [Dataview](https://github.com/blacksmithgu/obsidian-dataview)
- [Supercharged Links](https://github.com/mdelobelle/obsidian_supercharged_links) (optional)
It is not necessary to understand these plugins in detail, as the templates use them to automatically. If you stick to the templates in this repository, they will work fine without much tweaking. 

The "supercharged links" plugin is optional and will do nothing until you have everything set up. It is optional, but I highly recommend it - especially for project management templates.

More information can be found on my website. I will post new blog posts about Obsidian and my research in general.

# Templates
This section describes the templates in detail. 

The core plugin "Templates" supports variables, which are also used in these templates. Variables are marked in the template notes with `{{...}}` and will be replaced when inserting this template. More information can be found [here](https://help.obsidian.md/Plugins/Templates).

## Daily
The template "Daily" is for daily notes.
- [Dataview](https://github.com/blacksmithgu/obsidian-dataview): mandatory
- [Supercharged Links](https://github.com/mdelobelle/obsidian_supercharged_links): optional
### Metadata
- `type: daily`: 
  This is for filtering these notes.
- `tags: - todo`: 
  The tags metadata can contain several tags. Make sure that at least `todo` is a metadata.
- `date: {{date}}`: 
  Inserts the date in the format specified by the "Daily Notes" core plugin. Default: `YYYY-MM-DD`  (result format: "1970-01-01").
- `aliases`: 
  These are aliases under which your note can be found in the search pane (`ctrl+o`).
### Purpose
The purpose of this note is to record daily to-dos and to provide a quick overview of pending and upcoming tasks.

To display these tasks, this note uses dataviews in combination with the [todo template](ToDo.md). The most important metadata for using these dataviews is the `todo` tag.
### Setup
This template can be automatically inserted into the daily note. Check the settings of the "Daily Notes" core plugin and select this template as the "Daily Notes" template.

## Meeting
The template "Meeting" is for meeting notes.
- [Dataview](https://github.com/blacksmithgu/obsidian-dataview): optional
### Metadata
- `type: Meeting`: 
  This is for filtering these notes.
- `project`: 
  The projects where this meeting is held. This will be used by [project overview template](projects/projectOverview.md).
- `place`:
  The place the meeting is held.
- `duration`:
  The duration of the meeting.
- `date: {{date}}`: 
  Inserts the date in the format specified by the "Templates" core plugin. Default: `YYYY-MM-DD`  (result format: "1970-01-01")
- `participants`:
  The participants of the meeting.
- `aliases`: 
  These are aliases under which your note can be found in the search pane (`ctrl+o`).
- `recorder`:
  The recorder of the meeting.
- `protocol_ctime`:
  The creation time of the protocol.
### Purpose
The purpose of this note is to record meetings. It also has a header with the most important information. The header also shows some of the metadata as well. This is because when you export the protocol as PDF, the metadata is not displayed.


- Paper: If you want to write down information about a paper
- Topic: If you want to write down information about a topic
- For PhDs:
	- Student work specifications: To write down specifications about students work
	- Student work post: To write down a post for a student work