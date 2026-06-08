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

## New post (Typora)

Writing happens in [Typora](https://typora.io/) — open the repo folder or `_drafts/` in Typora's sidebar and edit without staring at raw Markdown syntax.

```bash
# Create a draft and open it in Typora
bin/new-post "Something I have opinions about"

# Preview drafts + live site locally
bundle exec jekyll serve --drafts --livereload

# When you're happy, move the draft into _posts/
bin/publish-post something-i-have-opinions-about

git add _posts && git commit && git push
```

Pages rebuilds in about a minute after push.

### Typora settings worth changing once

In **Typora → Settings**:

- **Files → On launch**: open `_drafts/` (or the whole repo) so posts show in the sidebar.
- **Image → When insert…**: copy to `assets/images/` (create the folder when you first need it).
- **Editor → Line wrap**: enabled (default) — matches how the blog reads on the web.

Manual fallback — `_posts/YYYY-MM-DD-some-slug.md` with YAML front matter (`bin/post-template.md` has the shape).

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
