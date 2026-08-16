# Site structure

## Current architecture

Art of Cyber AI is a dependency-free static site deployed from GitHub Pages at `https://artofcyberai.com/`.

| Surface | Location | Ownership | Current status |
|---|---|---|---|
| Homepage | `index.html` | Local | Live |
| Pre-training | `#pre-training` | Local | Card only; no archive or articles yet |
| Post-training | `https://trainrl.com/` | External | Live research blog |
| Inference | `#inference-details` | Local | Live homepage section |
| Research feed | `feed.xml` | Local | Live Atom feed |
| Search discovery | `sitemap.xml`, `robots.txt` | Local | Live |

## Repository files

```text
index.html             Homepage, metadata, lifecycle paths, work, about, feed CTA
styles.css             Shared design system plus dormant archive/article styles
script.js              Reveal, progress, parallax, active navigation, local time
feed.xml               Atom research feed
sitemap.xml            Google Search Console sitemap
robots.txt             Crawler rules and sitemap location
site.webmanifest       Install metadata and icons
CNAME                  GitHub Pages custom domain
favicon.ico            Browser icon
favicon-192.png        PWA icon
favicon-512.png        PWA icon
apple-touch-icon.png   Apple touch icon
og-image.png           Default social preview
```

## Homepage order

1. `#top` - hero and current work
2. `#manifesto` - point of view
3. `#research-paths` - Pre-training, Post-training, Inference
4. `#inference-details` - paged KV caching, continuous batching, fused kernels
5. `#notes` - featured post-training field note
6. `#alignment-note` - expanded note
7. `#work` - experience timeline
8. `#about` - biography and credentials
9. `#subscribe` - Atom feed subscription
10. Footer - contact and local time

## Planned Pre-training branch

Add this branch only when creating the first Pre-training blog:

```text
pre-training/
|-- index.html                  /pre-training/
`-- <article-slug>/
    `-- index.html              /pre-training/<article-slug>/
```

The archive owns discovery within the Pre-training path. Each article links back to the archive and to the homepage research paths. Keep Post-training calls to action pointed at `trainrl.com`.

## Existing visual system

- Paper background: `--paper: #e7dcc8`
- Light paper: `--paper-light: #f4ead8`
- Ink: `--ink: #1c211d`
- Accent red: `--red: #a23c2e`
- Muted text: `--muted: #63645c`
- Display/body serif: Iowan Old Style -> Palatino -> Georgia fallback
- Labels: Cascadia Mono -> SFMono -> Consolas fallback
- Supporting sans: Arial Narrow/Aptos Narrow stack
- Content width: `--page: min(1240px, calc(100vw - 64px))`
- Responsive breakpoints: 1000px and 760px

Prefer ruled borders, typographic hierarchy, restrained rotation, paper shadows, and small mono labels. Avoid glossy gradients, generic card grids, excessive rounded corners, and unrelated color additions.

## Content boundaries

Use these subjects to classify content:

- **Pre-training:** datasets, tokenization, objectives, scaling, architecture, optimization, distributed training, data quality, and foundation-model evaluation during training.
- **Post-training:** reinforcement learning, preference optimization, environments, graders, agent evaluation, alignment, and continual improvement. Publish this on TrainRL.
- **Inference:** serving, KV-cache management, batching, kernels, scheduling, quantization, latency, throughput, and GPU utilization.

When a topic spans paths, choose the path that owns the article's central mechanism and cross-link the related path instead of duplicating the article.
