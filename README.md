# tm.garcez.xyz

Personal website and blog built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.

**Live site:** [tm.garcez.xyz](https://tm.garcez.xyz/)

## Features

- Clean, minimal design with dark/light theme toggle
- Profile mode homepage with intro and quick links
- Blog posts with reading time estimates
- Career/CV page with downloadable PDF resume
- Links to public repositories and career projects
- Full-text search for posts
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
│   ├── css/            # Custom CSS overrides
│   └── cv/             # Downloadable CV PDF (hashed, see below)
├── content/
│   ├── about/          # About page
│   ├── cv/             # Career timeline
│   ├── posts/          # Blog posts
│   └── projects/       # Links to code and career projects
├── layouts/
│   └── partials/       # Theme template overrides
├── static/
│   ├── images/         # Profile and other images
│   ├── favicon.svg     # Site favicon
│   └── logo.svg        # Site logo
├── themes/
│   └── PaperMod/       # Theme (git submodule)
├── mise.toml           # Pinned Hugo version for local builds and CI
├── hugo.yaml           # Site configuration
└── CNAME               # Custom domain config
```

## Prerequisites

| Tool | Version | Why |
| --- | --- | --- |
| [mise](https://mise.jdx.dev/getting-started.html) | Current release | Installs the Hugo version in `mise.toml`. |
| [Hugo](https://gohugo.io/installation/) | `0.155.0` **extended** | The build tool. Installed through mise locally and in CI. |
| Git | Any recent | Fetches the theme submodule, and feeds `enableGitInfo` page timestamps. |

Hugo is the only build dependency. PaperMod uses plain CSS, so no Node or Dart
Sass step is needed. Local builds and CI use the extended edition.

PaperMod additionally requires Hugo `>= 0.146.0` (see `themes/PaperMod/theme.toml`).

### Install Hugo with mise

From the repository root:

```bash
mise trust
mise install
mise exec -- hugo version
```

`mise.toml` selects `hugo-extended = "0.155.0"`. The executable is still named
`hugo`; the version output should include `v0.155.0` and `+extended`.

`mise.lock` records the resolved downloads and checksums. Commit it whenever
you change `mise.toml`.

`mise exec --` loads the project's tools without requiring shell activation.
If mise is already activated in your shell, you can run `hugo` directly.

### Install Hugo without mise

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

2. Install Hugo with mise as described above.

## Local Development

```bash
mise exec -- hugo server -D
```

Open [http://localhost:1313](http://localhost:1313). The server live-reloads on
save. `-D` includes drafts, which production builds exclude via
`buildDrafts: false` in `hugo.yaml`.

## Building for Production

```bash
mise exec -- hugo --minify
```

The static site will be generated in the `public/` directory.

## Deployment

The site is deployed to GitHub Pages by `.github/workflows/hugo.yml`. CI uses
`jdx/mise-action` to install Hugo from the same `mise.toml` used locally. Push to
`main` (or run the workflow manually from the Actions tab) to trigger a deploy.
Pull requests build the site without deploying it.

### Upgrading Hugo

Update `hugo-extended` in `mise.toml`, run `mise install`, and verify with
`mise exec -- hugo --minify`. CI reads the same pin. The workflow pins the mise
installer version separately.

## Navigation

The header links to About, Career, and Posts. Home has About and Career buttons,
plus a compact CV download icon. Archive and Search are linked from Posts. The
Projects page remains available at `/projects/` but is not in the main menu.

Menu entries, homepage buttons, and social icons are configured in `hugo.yaml`.

## Creating New Content

```bash
mise exec -- hugo new posts/my-new-post.md
```

## Updating the CV PDF

Replace `assets/cv/tmgarcez-cv.pdf` and rebuild. The compact CV icon is configured
in `hugo.yaml` under `socialIcons`. The existing `layouts/partials/social_icons.html`
override hashes the PDF's bytes and appends the hash to its URL:

```html
<a href="/cv/tmgarcez-cv.pdf?v=e5669c29">
```

The URL changes when the PDF changes, so caches can distinguish versions. Keep
the PDF in `assets/`, not `static/`, so Hugo can read and publish it. The file
still publishes to `/cv/tmgarcez-cv.pdf`, and existing links keep resolving.

External links, `mailto:` links, and Hugo-generated paths such as `/index.xml`
do not need a content hash.

## Updating the Theme

PaperMod is pinned to a specific commit by the submodule. To move to the latest
upstream version:

```bash
git submodule update --remote themes/PaperMod
mise exec -- hugo server -D        # verify the site still renders
git add themes/PaperMod            # stage the new pinned commit
```

## Troubleshooting

**`Error: module "PaperMod" not found`** — the submodule was never fetched. Run
`git submodule update --init --recursive`. Confirm with `git submodule status`:
a leading `-` means uninitialized.

**Local site shows Page Not Found** — stop the server, initialise the PaperMod
submodule with `git submodule update --init --recursive`, then start it again with
`mise exec -- hugo server -D`.

**Mise reports an untrusted configuration** — review `mise.toml`, then run
`mise trust` from the repository root.

**`hugo: command not found`** — run `mise install`, then use
`mise exec -- hugo version`. Shell activation is optional when using `mise exec`.

**All pages share the same "last modified" date in production** — `enableGitInfo`
derives timestamps from git log, so the build needs full history. The deploy
workflow sets `fetch-depth: 0` on checkout for this reason; don't remove it. A
shallow clone collapses every page to the single fetched commit's date.

**Stale or odd rendering after an upgrade** — clear Hugo's caches with
`rm -rf public/ resources/` and rebuild. Both directories are generated and
gitignored.

## License

Content is copyright of the author. The [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme is licensed under MIT.
