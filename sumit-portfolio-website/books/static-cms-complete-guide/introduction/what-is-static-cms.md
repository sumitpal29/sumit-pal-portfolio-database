# What is Static CMS?

Static CMS is a Git-backed, zero-database content management system built for developers who want full ownership of their content without the overhead of a traditional CMS.

Instead of storing content in a database, Static CMS stores everything as plain files — Markdown for posts and documentation, JSON for structured data and metadata — directly inside a folder on your machine. You decide where that folder lives, and you decide if and how it gets published.

## The Core Idea

Most content management systems work like this:

Author writes → CMS stores in database → API reads from database → Frontend renders



Static CMS keeps it local and file-based:

Author writes → Files saved to your chosen folder → Metadata generated → Frontend reads from files



There is no server to maintain, no database to back up, and no account to manage. Your content is just a folder of plain text files.

## What You Get

- **A local visual editor** — A lightweight web UI (React + Express) you run on your machine to create and manage content.
- **A file-based content store** — All posts, books, custom data, and assets live as plain files in a project folder you configure.
- **An asset manager** — Upload images locally with drag-and-drop. Duplicate detection handles naming conflicts automatically with a replace-or-copy choice.
- **A metadata generator** — Produces paginated JSON index files so your frontend can list and search posts efficiently.
- **A JavaScript SDK** — A zero-dependency client library your frontend app uses to read content from the file store.

## What It Is Not

Static CMS is not a hosted service and does not manage Git operations for you. It is a local authoring tool — you run it on your own machine, manage your content folder, and handle publishing to wherever your frontend reads from. There is no account, no subscription, and no vendor lock-in. Your content is just files in a folder you control.