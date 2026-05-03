# Prerequisites

Before installing Static CMS, make sure your machine has the following.

## Required

**Node.js 18 or later**
Static CMS uses the native `fs/promises` API and ES module-compatible tooling. Node 18 is the minimum supported version.

Check your version:
```bash
node --version
```
If you need to install or upgrade Node, use the official installer at nodejs.org or a version manager like nvm or fnm.

npm 9 or later
npm ships with Node. It is used to install dependencies and run the dev servers.

```bash
npm --version
```
Recommended
A terminal you are comfortable with
Static CMS is started from the command line. Any terminal works — macOS Terminal, iTerm2, Windows Terminal, or the integrated terminal in VS Code.

VS Code or any text editor
The editor UI covers all common authoring workflows. However, having a text editor available is useful when you want to inspect raw Markdown or JSON files directly.

Git (optional)
Static CMS does not manage Git for you, but if you intend to version your content folder or publish to a Git host, having Git installed and configured is useful. Static CMS itself has no hard dependency on Git being present.

What You Do Not Need
A database (PostgreSQL, MySQL, MongoDB, etc.)
Docker
A cloud account or API key
A GitHub account (unless you plan to publish there)
Static CMS runs entirely on your machine with no external dependencies at runtime.


