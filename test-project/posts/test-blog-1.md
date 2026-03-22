---
title: test blog 1
slug: test-blog-1
createdAt: '2026-03-20T11:46:26.872Z'
updatedAt: '2026-03-20T11:46:26.872Z'
metadata:
  title: test blog 1
  description: sample description
  heroImage: ''
  draft: false
description: sample description
heroImage: ''
draft: false
---
# BlogDB

A Git-based, file-driven blog infrastructure built for developers.

Write in Markdown.
Store in Git.
Serve as JSON.

No database. No lock-in. Just files.

---

## ✨ What is BlogDB?

BlogDB is a **developer-first content system** where:

* Markdown files are your source of truth
* JSON files act as your API layer
* Git is your database
* Your UI is just a tool — not the owner

It turns your repository into a **portable, scalable content engine**.

---

## 🧠 Why BlogDB?

Most CMS platforms:

* hide your data
* require APIs
* lock you into their ecosystem

BlogDB does the opposite:

* your content lives in your repo
* everything is transparent
* your data is always yours

---

## ⚙️ How it works

### 1. Write content

Create blog posts using a clean markdown editor.

Each post becomes:

/projects/personal_blog/posts/my-post.md

---

### 2. Generate data

BlogDB reads all markdown files and generates:

/projects/personal_blog/meta/list_1.json
/projects/personal_blog/meta/list_2.json

These act as **ready-to-use APIs**.

---

### 3. Push to GitHub

Your repo becomes your backend.

---

### 4. Consume anywhere

Any app can fetch your content:

```bash
https://raw.githubusercontent.com/{user}/{repo}/main/projects/{project}/meta/list_1.json
```

---

## 🚀 Features

* Markdown-first workflow
* Git-based version control
* JSON API generation
* Pagination support
* Multi-project support
* Minimalist editor
* Zero database

---

## 📦 SDK (Client)

Use the official client:

```js
const client = createBlogClient({
  repo: "sumitpal/blog_database",
  project: "personal_blog"
});

const posts = await client.getPosts();
const post = await client.getPost("my-blog");
```

---

## 🏗️ Project Structure

```
/frontend
/backend
/projects
   /personal_blog
      /posts
      /meta
      config.json
/packages
   /client
```

---

## 🔥 What makes this different?

| Feature        | BlogDB     | Traditional CMS  |
| -------------- | ---------- | ---------------- |
| Data ownership | ✅ Yours    | ❌ Platform-owned |
| Storage        | Git        | Database         |
| API            | JSON files | Hosted API       |
| Portability    | High       | Low              |
| Lock-in        | None       | High             |

---

## 👥 Who is this for?

BlogDB is built for:

### 👨‍💻 Developers

* who prefer files over dashboards
* who want full control

### 🚀 Indie Hackers

* building fast, simple products
* no backend overhead

### 🧠 AI / Automation Systems

* clean structured JSON data
* easy ingestion

### 🌐 Multi-platform apps

* web
* mobile
* static sites

---

## ⚡ When should you use BlogDB?

Use it if you want:

* a blog without a backend
* a content system inside your repo
* fast, CDN-ready data
* full control over your content

---

## ❌ When NOT to use it

Avoid if you need:

* complex workflows (teams, roles)
* real-time editing
* heavy enterprise CMS features

---

## 🧭 Vision

BlogDB is not just a blog tool.

It’s a step toward:

> **Git as a universal content database**

---

## 🚀 Getting Started

```bash
npm install
npm run dev
```

---

## 🤝 Contributing

Open to ideas, improvements, and experiments.

---

## 📄 License

MIT
