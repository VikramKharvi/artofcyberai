---
name: artofcyberai-site
description: Maintain and extend the static Art of Cyber AI research website at artofcyberai.com. Use when working on its homepage lifecycle paths, missing Pre-training blog archive or posts, Inference notes, navigation, visual system, accessibility, technical SEO, Atom feed, sitemap, or GitHub Pages publishing structure.
---

# Art of Cyber AI site

Preserve the site as a research notebook spanning Pre-training, Post-training, and Inference. Keep changes static, lightweight, accessible, and consistent with the existing editorial design.

## Start every task

1. Read [references/site-structure.md](references/site-structure.md).
2. Inspect `git status` and the relevant HTML, CSS, JavaScript, feed, and sitemap files.
3. Identify which lifecycle path owns the requested content.
4. Make the smallest change that completes the request.
5. Validate locally before offering to publish.

Do not invent research results, citations, biography details, credentials, employers, or performance metrics. Preserve existing Search Console and analytics tags unless the user explicitly asks to replace them.

## Keep lifecycle ownership clear

- Host **Pre-training** research locally on `artofcyberai.com`.
- Keep **Post-training** links on `trainrl.com`; do not duplicate those articles locally.
- Keep **Inference** material local. Use `#inference-details` until the user requests a dedicated archive.

The Pre-training card currently has no blog destination. Do not leave a new archive unreachable: when creating the first Pre-training page, make the homepage card a link to `/pre-training/` and replace its "coming soon" status.

## Create Pre-training blogs

Use this default clean-URL structure:

```text
pre-training/
|-- index.html
`-- <article-slug>/
    `-- index.html
```

For the first post:

1. Create `pre-training/index.html` as the archive.
2. Create `pre-training/<article-slug>/index.html` as the article.
3. Reuse the existing journal classes in `styles.css`: `blog-page`, `blog-hero`, `blog-main`, `blog-article`, `article-lede`, and `article-section`.
4. Use root-relative assets such as `/styles.css`, `/script.js`, and `/favicon.ico` so nested URLs work.
5. Link the homepage Pre-training card to `/pre-training/`.
6. Add the article to the archive, `feed.xml`, and `sitemap.xml`.

Write research-first articles: define the technical problem, explain the mechanism, distinguish evidence from opinion, discuss tradeoffs and failure modes, and link primary sources. Avoid generic AI marketing language.

## Page contract

Every archive or article page must include:

- A skip link, primary navigation, one `<main>`, and a footer.
- A unique `<title>`, meta description, canonical URL, robots metadata, favicon links, feed discovery, and the existing analytics tag.
- Open Graph and Twitter metadata with absolute production URLs.
- `Blog` structured data for an archive or `BlogPosting` structured data for an article.
- One `<h1>`, logical heading order, descriptive links, visible keyboard focus, and meaningful image alt text.
- The paper, ink, rust-red, serif, mono-label, ruled-line, and restrained hand-drawn visual language already defined in `styles.css`.

Do not copy the homepage `ProfilePage` JSON-LD onto articles. Do not add new dependencies or a framework for a static page.

## Keep discovery files synchronized

When publishing an article:

1. Insert its Atom entry near the top of `feed.xml` and update the feed-level timestamp.
2. Add its canonical URL and last-modified date to `sitemap.xml`.
3. Update the Pre-training archive listing and count.
4. Update the homepage only when the new post changes a visible card or featured note.
5. Bump the `styles.css` query version only when CSS changed.

Keep Atom entries newest first and use the canonical article URL as the entry ID.

## Validate

Run proportionate checks before completion:

```text
git diff --check
python -m http.server 4173
```

Then verify:

- New and changed pages return HTTP 200 locally.
- Internal navigation, canonical URLs, feed links, and back links resolve.
- `feed.xml` and `sitemap.xml` parse as XML.
- Desktop and mobile layouts have no horizontal overflow, collapsed columns, or hidden reveal content.
- Keyboard navigation and reduced-motion behavior remain usable.
- The diff contains only requested changes.

Do not push or publish unless the user requests it or the surrounding task clearly includes deployment.
