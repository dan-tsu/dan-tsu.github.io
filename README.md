# dan-tsu.github.io

Daniel's personal blog — **LIVE** at https://dan-tsu.github.io. Astro (TypeScript, bun) on GitHub Pages, auto-deployed. This README is the as-built + update guide; read it before making changes.

## Stack & deploy

| Piece | Value |
|-------|-------|
| Generator | Astro `blog` template, TypeScript strict |
| Package manager | bun (never npm) |
| Host | GitHub Pages (free), user site `https://dan-tsu.github.io` |
| Repo | `github.com/dan-tsu/dan-tsu.github.io` (PUBLIC) |
| Local | `~/Projects/dan-tsu.github.io` |
| Deploy | `.github/workflows/deploy.yml` — push to `main` → bun build → Pages (~1 min) |
| Cost | €0. Custom domain later = `public/CNAME` + `site:` in astro.config + DNS. |

## Publish / update loop

1. Edit locally.
2. `bun run build` to verify. **If content/collection changed, clear the cache first:** `rm -rf node_modules/.astro .astro dist` (stale cache renders deleted posts).
3. `git commit` + `git push origin main`.
4. `gh run watch $(gh run list --limit 1 --json databaseId --jq '.[0].databaseId') --exit-status` — wait for deploy.
5. Verify live (see **Verification gotchas** — use Interceptor, not curl).

## Add a blog post

Create `src/content/blog/<slug>.md`. Filename = slug = URL `/blog/<slug>/`.

```yaml
---
title: "..."
description: "..."          # shown as the card excerpt + meta description
pubDate: "Jul 11 2026"
heroImage: "../../assets/<img>.jpg"   # optional; path relative to the .md file
tags: ["OTsecurity", "AI"]            # optional; feed the topic chips
---
```

Home "Latest writing", the blog index list, and the topic chips all update automatically.

## Structure

- `src/pages/index.astro` — home: thesis hero + auto "Latest writing" (5 most recent).
- `src/pages/blog/index.astro` — blog index: **left-rail "Blog" title** (hangs left of the post column, Miessler-style), self-counting subtitle, topic chips from tags, single-column horizontal cards, pagination (hidden until >15 posts), "Follow along" placeholder.
- `src/pages/about.astro` — About (no hero image).
- `src/components/Header.astro` — avatar (40px) + name + thin divider + LinkedIn icon → `linkedin.com/in/daniel-s1228/`. Nav links use `white-space: nowrap`.
- `src/components/Footer.astro` — © line at `0.8rem`.
- `src/layouts/BlogPost.astro` — post layout; hero via `<Image width={1224}>` (width-only preserves aspect — do NOT set both width+height or it squashes).
- `src/content.config.ts` — schema: `title, description, pubDate, updatedDate?, heroImage?, tags?`.
- `src/assets/` — `avatar.png` (pencil sketch), hero images.

## Hero images (Art skill)

- Generate with the **Art skill → Essay workflow** (`nano-banana-pro`). Landscape (3:2), no text in the prompt.
- API keys live in `~/.claude/PAI/.env` — **not** `~/.claude/.env`. `PAI_DIR=~/.claude/PAI`, and `Generate.ts` reads `${PAI_DIR}/.env`. Google billing is enabled (nano-banana-pro free-tier limit is 0); OpenAI key also present.
- **Deviations from the Art skill for THIS blog:** no "KAI" signature (that's another brand), and no sepia/transparent `--thumbnail` wiring (this is a white-background Astro blog — use a normal `heroImage`, not the CMS sepia scheme).
- nano-banana-pro tends to add text labels and a frame despite the prompt — strip with `sips` (ImageMagick/`cwebp` are NOT installed; `sips` is the available image tool). Convert `.png`→`.jpg` and crop borders with `sips`.

## Verification gotchas (this environment)

- **Interceptor screenshots fail when Chrome is minimized** (`window is minimized` / 45s timeout). Un-minimize + focus first: `osascript -e 'tell application "Google Chrome" to set minimized of every window to false'` then `... to activate`. (`eval`/`--text-only` work regardless.)
- **`curl` of the live site (esp. `/blog`) often hits a stale CDN edge** and reports false negatives after a successful deploy. Authoritative check = `interceptor eval --main` reading computed styles / rendered text.
