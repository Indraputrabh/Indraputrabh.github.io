# gh-page

My blog. Mostly rants.

Jekyll + GitHub Pages, dressed up to look like a circa-2008 WordPress install. Comments via Giscus (GitHub Discussions).

Live at <https://indraputrabh.github.io/>.

## Run it locally

```bash
bundle install
bundle exec jekyll serve --livereload
```

Then open <http://localhost:4000>.

## New post

`_posts/YYYY-MM-DD-some-slug.md`:

```yaml
---
title: "Something I have opinions about"
date: 2026-05-19 10:00:00 +0800
categories: [Rants]
tags: [opinion]
---

words
```

`git push` and Pages rebuilds in about a minute.

## Comments

Giscus stores comments as GitHub Discussions on this repo. Free, no ads, no separate account needed.

The repo is already wired up (`_config.yml` -> `giscus` block has the IDs). One click left:

1. Open <https://github.com/apps/giscus> and install it on `Indraputrabh/Indraputrabh.github.io`. That's it.

Commenters sign in with GitHub. If a visitor doesn't have a GitHub account, the comment box prompts them to sign up — it's free.

## Custom domain (for later)

1. Drop a `CNAME` file in the repo root with the domain, e.g. `blog.example.com`.
2. At the DNS provider, either point a subdomain CNAME at `indraputrabh.github.io`, or `A`/`AAAA` the apex at GitHub's [Pages IPs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site).
3. In repo Settings -> Pages, set the custom domain and tick "Enforce HTTPS" once the cert provisions.

## Layout

```
_config.yml      site config (title, giscus keys, etc.)
_layouts/        default / post / page
_includes/       header, footer, sidebar, comments, post-meta
_data/           nav.yml, blogroll.yml
_posts/          the actual writing
assets/css/      one SCSS file, no dependencies
index.html       paginated home
archive.html     by year
categories.html  by category
tags.html        tag cloud
404.html
```

No search backend, no recent-comments widget, no analytics. Add them when I miss them.
