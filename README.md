# tm.garcez.xyz

Personal website and blog built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.

**Live site:** [tm.garcez.xyz](https://tm.garcez.xyz/)

## Features

- Clean, minimal design with dark/light theme toggle
- Profile mode homepage with intro and quick links
- Blog posts with reading time estimates
- Career/CV page with downloadable PDF resume
- Projects showcase
- Full-text search
- Archive page
- RSS feed
- SEO optimized with sitemap and robots.txt
- LLM-friendly output format

## Project Structure

```
.
├── .github/
│   └── workflows/
│       └── hugo.yml    # Build and deploy to GitHub Pages
├── archetypes/         # Content templates
├── assets/
│   └── css/            # Custom CSS overrides
├── content/
│   ├── about/          # About page
│   ├── cv/             # Career timeline
│   ├── posts/          # Blog posts
│   └── projects/       # Projects showcase
├── layouts/
│   └── partials/       # Theme template overrides
├── static/
│   ├── cv/             # Downloadable CV PDF
│   ├── images/         # Profile and other images
│   ├── favicon.svg     # Site favicon
│   └── logo.svg        # Site logo
├── themes/
│   └── PaperMod/       # Theme (git submodule)
├── .tool-versions      # Pinned Hugo version (asdf)
├── hugo.yaml           # Site configuration
└── CNAME               # Custom domain config
```

## Prerequisites

| Tool | Version | Why |
| --- | --- | --- |
| [Hugo](https://gohugo.io/installation/) | `0.155.0` **extended** | The only build dependency. Pinned in `.tool-versions` and in CI. |
| Git | Any recent | Fetches the theme submodule, and feeds `enableGitInfo` page timestamps. |

Hugo is the whole toolchain — there is no `package.json`, and no Node or Dart Sass
step is needed. PaperMod ships plain CSS (no SCSS), so the regular Hugo edition
would build this site today. Use **extended** anyway: it is what CI builds with,
and keeping the two identical avoids surprises if SCSS or WebP processing is
added later.

PaperMod additionally requires Hugo `>= 0.146.0` (see `themes/PaperMod/theme.toml`).

### Install Hugo with asdf (recommended)

The pinned version lives in `.tool-versions`, so this is a one-time setup:

```bash
asdf plugin add hugo
asdf install            # reads .tool-versions
hugo version            # => hugo v0.155.0-... +extended
```

The edition is part of the asdf version string (`extended-0.155.0`) rather than a
separate setting, because asdf models exactly one version per tool.

### Install Hugo without asdf

```bash
brew install hugo
```

Homebrew's formula is built with the `extended` tag, but tracks the latest
release rather than the pinned one. To match CI exactly, download
`hugo_extended_0.155.0` from the
[v0.155.0 release](https://github.com/gohugoio/hugo/releases/tag/v0.155.0).

## Setup

1. Clone the repository with submodules — the PaperMod theme is a git submodule:
   ```bash
   git clone --recurse-submodules https://github.com/tmgarcez/tmgarcez.github.io.git
   cd tmgarcez.github.io
   ```

   Already cloned without `--recurse-submodules`? Fetch the theme now:
   ```bash
   git submodule update --init --recursive
   ```

   Skipping this leaves `themes/PaperMod/` empty and every build fails.

2. Install Hugo — see [Prerequisites](#prerequisites).

## Local Development

```bash
hugo server -D
```

Open [http://localhost:1313](http://localhost:1313). The server live-reloads on
save. `-D` includes drafts, which production builds exclude via
`buildDrafts: false` in `hugo.yaml`.

## Building for Production

```bash
hugo --minify
```

The static site will be generated in the `public/` directory.

## Deployment

The site is deployed to GitHub Pages by `.github/workflows/hugo.yml`. Push to
`main` (or run the workflow manually from the Actions tab) to trigger a deploy.

### Upgrading Hugo

The version is pinned in two places that must move together:

- `.tool-versions` — `hugo extended-<version>` (local builds)
- `.github/workflows/hugo.yml` — `HUGO_VERSION` (CI builds)

Bump both, run `asdf install`, then verify with `hugo --minify` before pushing.

## Creating New Content

```bash
hugo new posts/my-new-post.md
```

## Updating the Theme

PaperMod is pinned to a specific commit by the submodule. To move to the latest
upstream version:

```bash
git submodule update --remote themes/PaperMod
hugo server -D                     # verify the site still renders
git add themes/PaperMod            # commits the new pinned commit
```

## Troubleshooting

**`Error: module "PaperMod" not found`** — the submodule was never fetched. Run
`git submodule update --init --recursive`. Confirm with `git submodule status`:
a leading `-` means uninitialized.

**`No version is set for command hugo`** — asdf found no `.tool-versions` entry
for Hugo. Run the command from the repository root, and confirm `.tool-versions`
is present and lists `hugo extended-0.155.0`.

**`hugo: command not found` after `asdf install`** — the shim is missing. Run
`asdf reshim hugo`, and make sure asdf is initialized in your shell.

**All pages share the same "last modified" date in production** — `enableGitInfo`
derives timestamps from git log, so the build needs full history. The deploy
workflow sets `fetch-depth: 0` on checkout for this reason; don't remove it. A
shallow clone collapses every page to the single fetched commit's date.

**Stale or odd rendering after an upgrade** — clear Hugo's caches with
`rm -rf public/ resources/` and rebuild. Both directories are generated and
gitignored.

## License

Content is copyright of the author. The [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme is licensed under MIT.
