# ReaderFirst

A minimalist, reading-first Hugo theme optimized for both humans and AI agents.

![ReaderFirst screenshot](https://raw.githubusercontent.com/codertesla/ReaderFirst/main/images/screenshot.png)

ReaderFirst strips away every decoration that gets between the reader and the text. It ships with a clean typographic system, an automatic dark mode that follows the OS, an optional collapsible table of contents for long posts, and structured data (JSON-LD + JSON Feed) so your content is easy for both search engines and AI assistants to consume.

## Features

- **Minimalist** — One reading column, generous whitespace, and a restrained type scale. Nothing competes with the prose.
- **Adaptive dark mode** — Follows the visitor's `prefers-color-scheme` setting automatically, with no flash of incorrect theme on load.
- **AI-friendly** — Emits JSON-LD structured data (Article, BlogPosting, publisher) and a JSON Feed alongside the standard HTML and RSS outputs, so AI agents and search engines can parse your site reliably.
- **Table of contents** — An optional, collapsible outline generated from a post's headings. Opt in per post with `toc = true` in front matter; it renders inline at the top of the article with zero JavaScript.
- **Heading anchors** — Every content heading gets a stable `id` and a hover-revealed `#` permalink for easy deep-linking, via a Markdown render hook.
- **Code copy & language badge** — Every fenced code block gets a one-click copy button (vanilla JS, with `aria-live` confirmation) and a language label badge.
- **Image lightbox** — Click an article image to view it full-screen; Esc or click to close. Vanilla JS, no dependencies, no-op when a post has no images.
- **Breadcrumbs** — A minimal text trail (Home / Section / Title) above each post orientates the reader.
- **Multilingual & CJK** — Ships with English and Chinese translations; CJK content gets looser line-height, hanging punctuation, and automatic Han–Latin spacing. RTL languages are mirrored via logical CSS properties.
- **JSON Feed** — A `index.json` feed is published at the site root so feed readers and agents have a machine-readable subscription endpoint.
- **Accessible** — Semantic HTML, sensible heading order, and tested color contrast in both themes.
- **Fast** — No client-side JavaScript framework, no layout shift, just static HTML and a small CSS payload.

### Intentionally out of scope

To keep the theme light and reading-focused, the following are not bundled. Most can be added via the optional `layouts/partials/head/custom.html` hook or a user-supplied `assets/js/main.js`:

- **Comments** — no Disqus/Giscus/Remark42 wired in. Drop a comments partial into your site if needed.
- **Search** — no client-side search library. The JSON Feed at `/index.json` can serve as a search index for external tooling.
- **Analytics** — no GA/Plausible/etc. Inject your snippet via `partials/head/custom.html`.
- **Client-side JS framework** — none, by design. The only inline scripts are a no-flash theme resolver, the theme toggle, an optional TOC state memory, a per-post code-copy button, and an image lightbox; all vanilla, dependency-free.

## Installation

### As a Hugo Module (recommended)

Initialize modules in your site, then import ReaderFirst:

```bash
cd your-site
hugo mod init github.com/yourname/yoursite
```

Add to your site's `hugo.toml`:

```toml
theme = 'github.com/codertesla/ReaderFirst'

[module]
  [[module.imports]]
    path = 'github.com/codertesla/ReaderFirst'
```

Fetch the theme:

```bash
hugo mod get github.com/codertesla/ReaderFirst@v0.1.0
hugo mod tidy
```

To update later:

```bash
hugo mod get -u github.com/codertesla/ReaderFirst
hugo mod tidy
```

### As a Git Submodule

Add ReaderFirst to your existing Hugo site as a submodule:

```bash
cd your-site
git submodule add https://github.com/codertesla/ReaderFirst.git themes/ReaderFirst
git submodule update --init --recursive
```

Then enable it in your site's `hugo.toml`:

```toml
theme = 'ReaderFirst'
```

To update the theme later:

```bash
git submodule update --remote themes/ReaderFirst
```

### As a direct clone

If you prefer not to use modules or submodules:

```bash
cd your-site
git clone https://github.com/codertesla/ReaderFirst.git themes/ReaderFirst
```

## Basic Configuration

A minimal `hugo.toml` for a site using ReaderFirst:

```toml
baseURL = 'https://example.com/'
title = 'My Site'
theme = 'github.com/codertesla/ReaderFirst'

[module]
  [[module.imports]]
    path = 'github.com/codertesla/ReaderFirst'

[params]
  description = 'A minimalist, reading-first blog.'
  author = 'Your Name'
  mainSections = ['posts']

[taxonomies]
  tag = 'tags'
  category = 'categories'

[outputs]
  home = ['html', 'rss', 'json']

[outputFormats.JSON]
  mediaType = 'application/json'
  baseName = 'index'

[markup]
  [markup.highlight]
    # Token colors are defined (theme-aware) in the theme's CSS, so no `style`.
    noClasses = false
    lineNos = false
    tabWidth = 2
```

### Front matter reference

All fields are optional. Per-post front matter (TOML shown; YAML works too):

| Field     | Type     | Effect                                                                                     |
| --------- | -------- | ------------------------------------------------------------------------------------------ |
| `title`   | string   | Post title (heading, `<title>`, Open Graph, JSON-LD).                                       |
| `date`    | date     | Publish date; drives ordering, meta and reading time.                                       |
| `lastmod` | date     | Shows an "Updated" badge when it differs from `date`.                                       |
| `draft`   | bool     | `true` hides the post from builds and emits `noindex`.                                      |
| `author`  | string   | Byline; falls back to `params.author`. Used in meta and JSON-LD.                            |
| `tags`    | []string | Tag chips, `keywords` meta, JSON-LD `keywords`, and related-post matching.                  |
| `toc`     | bool     | `true` renders the collapsible outline at the top of the post.                              |
| `cover`   | string   | Path (or page-bundle `cover.*`/`featured.*`) used as the Open Graph / Twitter share image.  |
| `license` | string   | Adds a `license` field to the post's BlogPosting JSON-LD.                                    |

```toml
+++
title = 'My Post'
date = 2026-07-01
tags = ['hugo', 'markdown']
toc = true
+++
```

### Related posts

The post template shows up to three related posts (server-side, zero JS) based
on shared tags. Enable it by configuring Hugo's related-content index:

```toml
[related]
  includeNewer = true
  threshold = 80
  toLower = true
  [[related.indices]]
    name = 'tags'
    weight = 100
  [[related.indices]]
    name = 'date'
    weight = 10
```

### Optional site parameters

```toml
[params]
  description = 'A minimalist, reading-first blog.'
  author = 'Your Name'
  # publisherType = 'Person'               # 'Person' (personal blog) or 'Organization' (default). When 'Person', the JSON-LD publisher uses the author name and omits the logo.
  # logo = 'images/logo.png'              # populates publisher.logo in JSON-LD (Organization only)
  # default_og_image = 'images/og.png'    # fallback social share image
  # twitter = '@yourhandle'               # twitter:site meta
```

## Example Site

The `exampleSite/` directory contains a ready-to-run demo. From the theme repository root:

```bash
cd exampleSite
hugo mod tidy
hugo server
```

It imports the theme via Hugo Modules (`go.mod` uses a local `replace` so no GitHub fetch is needed during development).

## Theme Preview Images

Hugo Themes requires two preview images in the `images/` folder at the repository root:

- `images/screenshot.png` — 1500×1000 (3:2) full-screen capture of the theme.
- `images/tn.png` — 900×600 (3:2) thumbnail used in the themes gallery.

These images are located in the `images/` folder and will be used automatically by the Hugo Themes gallery.
## License

ReaderFirst is released under the [MIT License](LICENSE).
