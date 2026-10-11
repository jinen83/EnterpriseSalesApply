source "https://rubygems.org"

# GitHub Pages builds Jekyll natively on push. Pinning the `github-pages`
# gem keeps local builds in lockstep with GitHub's hosted toolchain
# (Jekyll version, plugins, and Sass converter) so what builds here builds there.
gem "github-pages", group: :jekyll_plugins

# Jekyll plugins activated via _config.yml.
group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-seo-tag"
  gem "jekyll-sitemap"
end

# Ruby 3.0+ no longer ships WEBrick, which `jekyll serve` needs for local preview.
gem "webrick", "~> 1.8"
