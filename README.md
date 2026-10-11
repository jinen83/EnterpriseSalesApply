# Enterprise Sales Apply

The **Enterprise Sales Apply** blog — field notes, playbooks, and lessons on
running an enterprise sales motion that scales. Built as a
[Jekyll](https://jekyllrb.com/) site and hosted on **GitHub Pages**, which
builds Jekyll natively on every push (no custom CI required).

## What's here

- A mobile-first design system (`assets/css/main.scss`) with a constrained
  reading measure, a modular heading scale, accessible light/dark contrast,
  and responsive listing cards.
- A shared layout (`_layouts/default.html`) with header, primary nav, and
  footer, plus a `<head>` include (`_includes/head.html`) wired for SEO and
  RSS metadata.
- A home page (`index.html`) that lists posts as cards and shows an empty
  state until the first post lands.

## Prerequisites

- **Ruby** 2.7+ (3.0+ recommended) with development headers
- **Bundler** (`gem install bundler`)

## Install

From the repository root:

```sh
bundle install
```

## Run locally

```sh
bundle exec jekyll serve
```

Then open <http://localhost:4000>. The server live-reloads most content
changes; restart it after editing `_config.yml`.

## Build

Generate the static site into `_site/`:

```sh
bundle exec jekyll build
```

Add `--strict_front_matter` to fail the build on any malformed front matter:

```sh
bundle exec jekyll build --strict_front_matter
```

## Writing posts

Add Markdown files under a `_posts/` directory named
`YYYY-MM-DD-title.md` with front matter:

```markdown
---
title: Your post title
date: 2026-01-01
---

Your content here.
```

Posts automatically appear as cards on the home page and in the RSS feed
(`/feed.xml`).

## Deploy

Push to the branch GitHub Pages is configured to build (commonly `main` or
`gh-pages`). GitHub Pages builds and publishes the Jekyll site automatically.
Set `url` and `baseurl` in `_config.yml` to match your Pages URL — use
`baseurl: "/EnterpriseSalesApply"` for a project page, or leave it empty for a
user/organization page.

## Configuration

Site-wide settings (title, description, author, plugins, permalinks) live in
`_config.yml`. Jekyll reads it once at startup, so restart the build or server
after changing it.
