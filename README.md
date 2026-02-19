# tm.garcez.xyz

Personal website and blog built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.

**Live site:** [tm.garcez.xyz](https://tm.garcez.xyz/)

## Features

- Clean, minimal design with dark/light theme toggle
- Blog posts with reading time estimates
- Full-text search
- Archive page
- RSS feed
- SEO optimized with sitemap and robots.txt
- LLM-friendly output format

## Project Structure

```
.
├── archetypes/        # Content templates
├── assets/
│   └── css/           # Custom CSS overrides
├── content/
│   ├── about/         # About page
│   └── posts/         # Blog posts
├── static/            # Static assets
├── themes/
│   └── PaperMod/      # Theme (git submodule)
├── hugo.yaml          # Site configuration
└── CNAME              # Custom domain config
```

## Prerequisites

- [Hugo](https://gohugo.io/installation/) (extended version recommended)
- Git

## Local Development

1. Clone the repository with submodules:
   ```bash
   git clone --recurse-submodules https://github.com/tmgarcez/tmgarcez.github.io.git
   cd tmgarcez.github.io
   ```

2. Start the development server:
   ```bash
   hugo server -D
   ```

3. Open [http://localhost:1313](http://localhost:1313) in your browser.

## Building for Production

```bash
hugo --minify
```

The static site will be generated in the `public/` directory.

## Deployment

The site is deployed to GitHub Pages. Push changes to the `main` branch to trigger deployment.

## Creating New Content

```bash
hugo new posts/my-new-post.md
```

## License

Content is copyright of the author. The [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme is licensed under MIT.
