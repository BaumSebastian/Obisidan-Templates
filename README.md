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
### Meta data
- `type: daily`: this is for filtering these notes
- `tags: - todo`: Can contain multiple tags, but at least the tag todo, to add it to its to do list.
- `date: {{date}}`: Inserts the date with the format specified by the daily core plugin. Default: `YYYY-MM-DD` with would result in "1970-01-01"
- `aliases`: These are names that can also be searched with `ctrl+o`.
### Purpose
This note purpose is to write down daily notes and give a quick overview over pending tasks and near future tasks. To use these two queries optimal, use the [todo template](ToDo.md) as it provides the todo tag as well as other information. 

### Setup
This can be turned on automatically with: `settings` > (core plugins) `Daily notes` > `Template file location` 


- Meeting: For meetings
- Paper: If you want to write down information about a paper
- Topic: If you want to write down information about a topic
- For PhDs:
	- Student work specifications: To write down specifications about students work
	- Student work post: To write down a post for a student work