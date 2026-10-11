<!-- source-commit: 46821e1d4644539d311a1a094d6699083b5b3157 -->
# Repo learnings

Compounding failure diary for this Jekyll + GitHub Pages site. High-signal gotchas only.

## Gotchas
- Ruby is NOT preinstalled in the agent sandbox. Install before any `bundle`
  command: `apt-get update && apt-get install -y ruby-full build-essential`,
  then `gem install bundler`. `bundle install` fails with "command not found" otherwise.
- `assets/css/main.scss` MUST start with an (even empty) `---` front-matter
  block, or Jekyll skips the Sass converter and never emits
  `_site/assets/css/main.css` — the site then loads with no styles.
- Pin the `github-pages` gem (not bare `jekyll`) so local builds match GitHub's
  hosted toolchain; it currently resolves to Jekyll 3.10, which uses the Ruby
  `sass` converter (not dart-sass) — nested `//` comments and CSS custom
  properties are fine, but `@use`/`@forward` (dart-sass only) will NOT compile.
- Ruby 3.0+ dropped bundled WEBrick; `jekyll serve` crashes with
  `cannot load such file -- webrick` unless `gem "webrick"` is in the Gemfile.
  `jekyll build` does not need it.
- `CLAUDE.md` (and anything else) publishes into `_site/` unless listed under
  `exclude:` in `_config.yml`. Add repo-only files there.
- GitHub Pages builds Jekyll natively on push — no Actions workflow or custom CI
  needed. Set `url`/`baseurl` in `_config.yml`: `baseurl: "/EnterpriseSalesApply"`
  for a project page, empty for a user/org page, or asset links 404.
- Rebranding via `_config.yml` alone is NOT enough: `_posts/*.md` may hardcode
  `author:` in front matter, which `_includes/post-meta.html` (`page.author |
  default: site.author`) and the jekyll-feed entry `<author>` render as the OLD
  brand on post pages and in `feed.xml`. Symptom: new brand everywhere except the
  post byline/feed entry author. Fix: drop the per-post `author:` line so it
  inherits `site.author`, then grep `_site/` for the old brand to confirm.
