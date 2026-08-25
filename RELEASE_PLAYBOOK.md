# Research release playbook

The website and Pressmaster handle different parts of the release:

- GitHub Pages controls whether a research blog is public.
- Pressmaster creates and schedules the social posts that announce it.

## Current public state

- Pre-trained: archive-status landing page only.
- Post-trained: `post-training-stack.html` is the only public blog.
- Inference: archive-status landing page only.
- The full libraries are preserved on `archive/full-library-2026-08-24` in their respective repositories.

## Recommended cadence

Start with one research blog each week. Publish the website first, then schedule the matching Pressmaster post later the same day. Review Pressmaster performance after four releases before changing the cadence.

Pressmaster currently has connected social channels and a queue of TrainRL ideas. Use its Calendar or **Plan Ahead** flow for promotion; do not use it as the source of truth for which website files are public.

## Release checklist

1. Choose one blog from the archived library.
2. Restore only that page to the site's `main` branch.
3. Add one visible link on that site's landing page.
4. Add only the new public URL to its `sitemap.xml`.
5. Add the new release to `artofcyberai.com/feed.xml`.
6. Add the URL to the homepage assistant fallback corpus. The research sites also discover public pages through the three sitemaps.
7. Run:

   ```text
   python work/audit_lifecycle_sites.py
   python <site>/scripts/blog_tool.py check
   ```

8. Merge or push the website release.
9. After the live URL returns 200, schedule its matching Pressmaster promotion.

## Important visibility note

Removing an article from GitHub Pages prevents normal website access and discovery. If the repository and its archive branch are public, the source still remains visible to someone browsing GitHub. Use a private editorial repository if unpublished drafts must be confidential.
