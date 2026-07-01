# ReaderFirst

A minimalist, reading-first Hugo theme optimized for both humans and AI agents.

ReaderFirst strips away every decoration that gets between the reader and the text. It ships with a clean typographic system, an automatic dark mode that follows the OS, a floating table of contents for long posts, and structured data (JSON-LD + JSON Feed) so your content is easy for both search engines and AI assistants to consume.

## Features

- **Minimalist** — One reading column, generous whitespace, and a restrained type scale. Nothing competes with the prose.
- **Adaptive dark mode** — Follows the visitor's `prefers-color-scheme` setting automatically, with no flash of incorrect theme on load.
- **AI-friendly** — Emits JSON-LD structured data (Article, BlogPosting, publisher) and a JSON Feed alongside the standard HTML and RSS outputs, so AI agents and search engines can parse your site reliably.
- **Table of contents** — An automatic, scroll-aware TOC is generated from your post headings and pinned beside the article for easy navigation.
- **JSON Feed** — A `index.json` feed is published at the site root so feed readers and agents have a machine-readable subscription endpoint.
- **Accessible** — Semantic HTML, sensible heading order, and tested color contrast in both themes.
- **Fast** — No client-side JavaScript framework, no layout shift, just static HTML and a small CSS payload.

## Installation

### As a Git Submodule (recommended)

Add ReaderFirst to your existing Hugo site as a submodule so it stays easy to update:

```bash
cd your-site
git submodule add https://github.com/sos/hugo-theme-reader-first.git themes/ReaderFirst
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

If you prefer not to use submodules:

```bash
cd your-site
git clone https://github.com/sos/hugo-theme-reader-first.git themes/ReaderFirst
```

## Basic Configuration

A minimal `hugo.toml` for a site using ReaderFirst:

```toml
baseURL = 'https://example.com/'
languageCode = 'en-us'
title = 'My Site'
theme = 'ReaderFirst'

[params]
  description = 'A minimalist, reading-first blog.'
  author = 'Your Name'

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
    noClasses = false
    style = 'github'
    lineNos = false
    tabWidth = 2
```

### Table of contents

To show a TOC on a post, set `toc = true` in its front matter:

```toml
+++
title = 'My Post'
toc = true
+++
```

### Optional site parameters

```toml
[params]
  description = 'A minimalist, reading-first blog.'
  author = 'Your Name'
  # logo = 'images/logo.png'              # populates publisher.logo in JSON-LD
  # default_og_image = 'images/og.png'    # fallback social share image
  # twitter = '@yourhandle'               # twitter:site meta
```

## Example Site

The `exampleSite/` directory contains a ready-to-run demo. From the theme repository root:

```bash
cd exampleSite
hugo server
```

It uses `themesDir = "../.."` so it loads the theme directly from the parent folder without installing anything.

## Theme Preview Images

Hugo Themes requires two preview images in the `images/` folder at the repository root:

- `images/screenshot.png` — 1500×1000 (3:2) full-screen capture of the theme.
- `images/tn.png` — 900×600 (3:2) thumbnail used in the themes gallery.

These images are located in the `images/` folder and will be used automatically by the Hugo Themes gallery.
## License

ReaderFirst is released under the [MIT License](LICENSE).
