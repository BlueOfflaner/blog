# Hexo Personal Blog

This repository contains a Hexo-based personal blog with the Butterfly theme and GitHub Pages deployment workflow.

## Local development

```bash
npm install
npm run server
```

Open `http://localhost:4000`.

## Build static files

```bash
npm run build
```

Generated files are in `public/`.

## GitHub Pages deployment

1. Ensure `_config.yml` is set correctly:
   - `url: https://blueofflaner.github.io`
   - `root: /`
2. Push to `main`.
3. In GitHub repo settings, set Pages source to `GitHub Actions`.

The workflow file is `.github/workflows/deploy-pages.yml`.

## Post and image convention

This project uses `post_asset_folder: true`, so each post can keep images in its own folder.

### Create a post

```bash
npx hexo new post "my-post-title"
```

This creates:

- `source/_posts/my-post-title.md`
- `source/_posts/my-post-title/` (asset folder)

### Image storage rules

1. Store images only in the post asset folder:
   - `source/_posts/my-post-title/`
2. Use lowercase kebab-case file names:
   - `cover.webp`
   - `architecture-diagram.webp`
   - `result-v1.png`
3. Reference images with relative paths in markdown:
   - `![cover](./cover.webp)`
4. Keep one cover image per post, named `cover.webp`.

### Image format and size rules

1. Prefer `webp` for screenshots/photos.
2. Use `png` only when transparency or sharp line art is required.
3. Recommended max width:
   - Cover: `1600px`
   - In-article images: `1200px`
4. Target file size:
   - Cover: `<= 300 KB`
   - In-article image: `<= 200 KB`

### Pre-publish checklist

1. `npm run server` and verify all images load.
2. `npm run build` and ensure no broken image links.
3. Commit both markdown file and image assets together.
