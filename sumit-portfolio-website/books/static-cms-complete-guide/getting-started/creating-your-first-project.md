# Creating Your First Project

Once the editor is running at `http://localhost:5173`, the first thing you do is create a project. A project is the top-level container for all your content — posts, books, custom data, and assets.

## What is a Project?

A project maps to a single folder on your machine. Everything inside that folder is plain files: Markdown for content, JSON for metadata and config, and image files for assets. You choose where this folder lives when you create the project.

One instance of Static CMS can manage multiple projects. Each project is independent — separate config, separate posts, separate assets.

## Creating a Project

1. On the home screen, click **New Project**.
2. Fill in the project details:

| Field          | Description                                                                 |
|----------------|-----------------------------------------------------------------------------|
| **Name**       | A human-readable label shown in the editor UI.                              |
| **Folder path**| The absolute path on your machine where the project folder will be created. |

3. Click **Create**.

The editor creates the folder at the path you specified with a default structure:
```bash
your-chosen-path/
├── config.json
├── posts/
├── meta/
├── books/
└── assets/
```


The project now appears on the home screen and is ready to use.

## Project Config

Each project has a `config.json` at its root. You can edit it from the **Settings** tab inside the project. The default values are:

```json
{
  "pageSize": 10,
  "sortOrder": "desc",
  "contentPath": "posts",
  "metaPath": "meta"
}
Field	Default	Description
pageSize	10	Number of posts per generated metadata page.
sortOrder	"desc"	Sort order for posts in metadata: desc or asc.
contentPath	"posts"	Subfolder where post Markdown files are stored.
metaPath	"meta"	Subfolder where generated JSON index files go.
Managing Projects
From the home screen you can:

Rename a project — click the rename icon next to the project name and type a new name. This renames the display label only; the folder on disk is not moved.
Delete a project — click the delete icon and confirm in the modal. This removes the project from the editor. The folder on disk is also deleted, so confirm before proceeding.
Open a project — click its name to enter the project dashboard.