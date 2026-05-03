# When to Use Static CMS

Static CMS is a deliberate trade-off. Understanding where it fits well (and where it does not) will save you time.

## Good Fits

**Personal blogs and portfolios**
You control the content folder, write at your own pace, and want zero infrastructure cost. Static CMS was built for exactly this use case.

**Developer documentation**
The Books feature is designed for multi-chapter, nested documentation. If you are writing a guide, a technical spec, or an API reference, it handles the structure for you.

**Small to medium content sites**
Sites with hundreds of posts work fine. The pagination system generates efficient JSON indexes so frontends do not load everything at once.

**Headless setups with any frontend framework**
Because content is served from plain files, your frontend can be anything — Next.js, Astro, SvelteKit, plain HTML. The SDK works in any JavaScript environment.

**Content that lives alongside code**
When your content and your codebase belong together — changelogs, release notes, in-repo wikis — Static CMS fits naturally into a local-first workflow.

**Developers who want full control over publishing**
Static CMS does not impose a publishing mechanism. You decide how and where to move your content folder — commit it to Git, rsync it to a server, upload it to an S3 bucket. The tool authors; you publish.

## Not the Right Tool For

**Multiple non-technical editors**
There is no authentication, no roles, and no hosted UI. Everyone editing needs to run the local tool. If your team includes non-developers who expect a hosted CMS URL, look elsewhere.

**Real-time or user-generated content**
Comments, reactions, user profiles, live data — none of this belongs in a static file store. Static CMS is read-heavy content authored by you, not your users.

**Content requiring fine-grained access control**
Static CMS has no access control layer. If your content needs to be gated or private, you will need to handle that at the publishing and serving layer independently.

**High-frequency publishing with automated pipelines**
Static CMS is a manual, editor-driven tool. If your publishing flow is fully automated or requires programmatic content creation at scale, you need a headless CMS with a proper write API.

## The Honest Summary

Static CMS trades collaboration features and managed publishing for simplicity, zero cost, and full file ownership. If you are a developer who wants your content to be plain files on your machine — with a decent editor and a clean SDK to consume it — it is exactly the right tool.