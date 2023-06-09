![banner](obsidian_banner.png)

# Obsidian Templates

This repository contains templates for Obsidian notes.

- Why Obsidian: Watch following from [linking your thinking](https://www.youtube.com/@linkingyourthinking/featured):
  [Video](https://www.youtube.com/watch?v=QgbLb6QCK88)
- Why Templates: Speed up your process when working with obsidian.

# How to use these Templates

Templates are a highly dynamic part of Obsidian and change over time. I try to keep everything working, but it can happen that really old templates may not work with newer templates.

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
Some templates (like [Daily Note template](#daily-note-template)) require additional settings. This is indicated by a "Setup" section in the template.

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

## Daily Note

<details>

File: [Daily.md](Daily.md). The template "Daily" is for daily notes.

- [Dataview](https://github.com/blacksmithgu/obsidian-dataview): mandatory
- [Supercharged Links](https://github.com/mdelobelle/obsidian_supercharged_links): optional

### Metadata of Daily Note

- `type: daily`:
  This is for filtering these notes.
- `tags: - todo`:
  The tags metadata can contain several tags. Make sure that at least `todo` is a metadata.
- `date: {{date}}`:
  Inserts the date in the format specified by the "Daily Notes" core plugin. Default: `YYYY-MM-DD`  (result format: "1970-01-01").
- `aliases`:
  These are aliases under which your note can be found in the search pane (`ctrl+o`).

### Purpose of Daily Note

The purpose of this note is to record daily to-dos and to provide a quick overview of pending and upcoming tasks.

To display these tasks, this note uses dataviews in combination with the [todo template](ToDo.md). The most important metadata for using these dataviews is the `todo` tag.

### Setup of Daily Note

This template can be automatically inserted into the daily note. Check the settings of the "Daily Notes" core plugin and select this template as the "Daily Notes" template.

</details>

## Meeting Note

<details>

File: [Meeting.md](Meeting.md). The template "Meeting" is for meeting notes.

- [Dataview](https://github.com/blacksmithgu/obsidian-dataview): optional

### Metadata of Meeting Note

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

### Purpose of Meeting Note

The purpose of this note is to record meetings. It also has a header with the most important information. The header also shows some of the metadata as well. This is because when you export the protocol as PDF, the metadata is not displayed.

</details>

## ToDo Note

<details>

File: [ToDo.md](ToDo.md). The template "ToDo" is for to-do notes.

- [Dataview](https://github.com/blacksmithgu/obsidian-dataview): optional - recommended
- [Supercharged Links](https://github.com/mdelobelle/obsidian_supercharged_links): recommended

### Metadata of ToDo Note

- `tags: - todo`:
  The tags metadata can contain several tags. Make sure that at least `todo` is a metadata.
- `date: {{date}}`:
  Inserts the date in the format specified by the "Templates" core plugin. Default: `YYYY-MM-DD`  (result format: "1970-01-01"). It can also be referred as creation time with `this.file.ctime`.
- `due`:
  The deadline of the to-do.
- `status`:
  The status of the to-do. It is highly recommended to use the supercharged links plugin to display the status next to a link. See my website for more information.

### Purpose of ToDo Note

The purpose of this note is to give your general to-do a note of its own. Each task in your to-do note is displayed in the daily note. You can view these tasks in your to-do note as sub-steps to achieving the main goal.

If you are using the [Dataview](https://github.com/blacksmithgu/obsidian-dataview) plugin, you can extend the sub-tasks by adding the short hand syntax supported by Dataview. It is explained [here](https://blacksmithgu.github.io/obsidian-dataview/annotation/metadata-tasks/) and supports task specific due, completion, creation, start and scheduled dates. The `due` metadata is also set in the note, but is overridden by a `due` on a specific sub-task.

</details>

## Topic Note

<details>

File: [Topic.md](Topic.md). The template "Topic" is for notes about general topics.

### Metadata of Topic Note

- `type:`:
- The type metadata is to define the type of topic this note is about.
- `tags:`:
  The tags metadata can contain several tags.
- `date: {{date}}`:
  Inserts the date in the format specified by the "Templates" core plugin. Default: `YYYY-MM-DD`  (result format: "1970-01-01"). It can also be referred as creation time with `this.file.ctime`.

### Purpose of Topic Note

The purpose of this note is to write notes about any topic.

</details>

___
The `Literature` and `projects` section is under construction.
