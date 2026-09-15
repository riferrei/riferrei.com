# riferrei.com

Personal site of Ricardo Ferreira, built with [Hugo](https://gohugo.io/) and the
[hugo-theme-devrel](https://github.com/dadoonet/hugo-theme-devrel) theme
(a DevRel overlay on the Dream theme). Migrated from WordPress.

## Prerequisites

- [Hugo extended](https://gohugo.io/installation/) v0.166+ (`hugo version` should say `+extended`)
- [Go](https://go.dev/dl/) 1.23+ (the theme is a Hugo module and needs Go to resolve dependencies)
- Node.js 22+ (only for the Pagefind search index)

## First-time setup

This repo is a Hugo module. The theme is pulled automatically the first time you
resolve modules; it is not vendored here.

```
# 1. Download the post images from the old WordPress site into their bundles.
#    (Run once. Safe to re-run; existing files are skipped.)
./fetch-images.sh

# 2. Resolve the theme module (needs Go + network).
hugo mod get -u
hugo mod tidy

# 3. Run locally.
hugo server
```

Open http://localhost:1313.

If `hugo server` complains about the search index on first run, build it once:

```
hugo --gc --minify
npx pagefind --site public
```

## Content

### Posts

```
content/posts/YYYY-MM-DD-slug/index.md      # the post
content/posts/YYYY-MM-DD-slug/*.png|jpg     # images live next to the post
```

Create a new one:

```
hugo new posts/YYYY-MM-DD-my-post/index.md
```

All 32 published WordPress posts were migrated as page bundles. Images referenced
in each post were rewritten to bundle-relative filenames; `fetch-images.sh` pulls
them down. Three posts carry a `cover:` (their WordPress featured image).

### Talks

```
content/talks/YYYY/YYYY-MM-DD-event/index.md
```

Three sample talks are scaffolded (All Things Open 2025, Kafka Summit SF 2019,
and a 2022 session). Each has `# TODO` markers for the fields that could not be
migrated automatically: exact session titles, conference coordinates, PDF slide
paths, and YouTube IDs. Fill those in, or add new talks with
`hugo new talks/YYYY/YYYY-MM-DD-event/index.md`.

The map (`/talks/map`) needs `conference.latitude` / `longitude`. The videos
page (`/talks/videos`) lists only talks that set `youtube:`.

### About

```
content/about/index.md        # shell
content/about/10-me.md        # sections, sorted by filename prefix
content/about/20-speaking.md
content/about/30-opensource.md
data/socials.toml             # social links
content/about/ricardo.jpg     # <-- add your avatar here (referenced by params.avatar)
```

## Deploy (GitHub Pages)

A workflow at `.github/workflows/pages.yml` builds Hugo + Pagefind and deploys on
every push to `main`.

One-time repo configuration:

1. Push this repo to `github.com/riferrei/riferrei.com`.
2. **Settings -> Pages -> Source** = *GitHub Actions*.
3. **Settings -> Pages -> Custom domain** = `riferrei.com`, then enable **Enforce HTTPS**.
4. DNS for the apex domain (`riferrei.com`), at your DNS host:
   - Point the apex to GitHub Pages with the four A records and four AAAA records
     from [GitHub's docs](https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain),
     **or** use an ALIAS/ANAME record to `riferrei.github.io` if your host supports it.
   - `static/CNAME` in this repo already contains `riferrei.com`.

Note: since this is a **project** repo (not `riferrei.github.io`), the custom
domain is what makes it serve at the apex. Do not rename the repo to
`riferrei.github.io` unless you intend it to be your user site.

## Migration notes

- Source: WordPress WXR export (`ricardoferreira_WordPress_2026-09-15.xml`).
- 32 published posts migrated. Gutenberg block markup was stripped and the HTML
  converted to Markdown; `[code]` blocks became fenced code blocks.
- Not migrated: 4 private + 2 draft posts, and WordPress-only pages (Home, Blog,
  Speaking Calendar). The speaking calendar lived on a subdomain; recreate it as
  talks if you want it back.
- Old subdomains (`videos.`, `code.`, `talks.`, `calendar.`) are now consolidated
  into this single site's Posts / Talks / Videos sections.
