# How It Works

Static CMS has three moving parts that work together: the **Editor**, the **Projects folder**, and the **SDK**.

## The Editor (Local Dev Tool)

The editor is a React + Express app you run locally. It provides a visual interface for:

- Creating and managing projects
- Writing posts in Markdown with a live preview
- Structuring multi-chapter books and documentation
- Uploading and managing image assets
- Storing custom JSON data alongside your content

The backend runs on `localhost:4000` and the UI on `localhost:5173`. You only run this when you are actively writing or editing — it is not a production server.

## The Projects Folder

When you create a project, you choose where its folder lives on your machine. Everything created in the editor is saved there as plain files. Each project has a predictable layout:
```
my-project/
├── config.json          # Project settings
├── posts/               # Markdown blog posts
├── meta/                # Auto-generated pagination JSON
├── books/               # Hierarchical documentation
├── assets/              # Uploaded images
└── custom-data-folder/  # Any JSON data you define
```


This is a plain folder — no hidden state, no proprietary format. You can open it in any text editor, commit it to version control, or copy it anywhere.

## Assets and Image Storage

Images are uploaded directly to the `assets/` subfolder of your project via the Assets page. The upload flow handles common friction points automatically:

- **Filename sanitisation** — Spaces, special characters, and uppercase letters in the original filename are normalised to a safe slug (e.g. `My Photo (1).PNG` becomes `my-photo-1.png`).
- **Duplicate detection** — If a file with the same name already exists, the editor pauses and shows a conflict dialog. You choose to either replace the existing file or save the new one under a suggested copy name (e.g. `my-photo-copy-1.png`).
- **Local preview** — Uploaded images are immediately browsable via the local server with thumbnail previews and a lightbox view.
- **20 MB limit** — The upload endpoint enforces a 20 MB per-file cap. Supported formats are JPEG, PNG, GIF, WebP, SVG, and AVIF.

## Metadata Generation

After writing or editing content, you run the **Generate** step from the editor. This scans all posts and produces:

- `meta/index.json` — Pagination index (total pages, post count)
- `meta/list_1.json`, `meta/list_2.json`, … — One file per page, each containing the post list with frontmatter for that page

Your frontend reads these files directly — no backend API needed at runtime.

## The SDK

The JavaScript SDK wraps the file reads into a clean API. You install it in your frontend app (React, Next.js, Astro, or any framework) and call methods like `getPosts()`, `getPost(slug)`, or `search(query)`. It handles URL construction, JSON parsing, Markdown frontmatter extraction, and in-memory caching automatically.

## The Full Flow

Open editor locally
Write post / edit book / upload image
Click "Generate" → meta/index.json and meta/list_*.json are created
Frontend SDK reads from your content folder → content is live


How you publish (copying to a server, committing to a repo, syncing to a CDN) is entirely up to you. Static CMS focuses on the authoring and structure layer — the publishing step is yours to own.