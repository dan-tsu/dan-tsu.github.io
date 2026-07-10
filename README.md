# dan-tsu.github.io

Daniel's blog. Built with [Astro](https://astro.build) (TypeScript, bun), deployed
free to GitHub Pages. **Not live yet** — built and staged locally, holding for a
first post and a settled topic.

## What this is (as-built)

| Piece | Value |
|-------|-------|
| Generator | Astro `blog` template, TypeScript strict |
| Package manager | bun |
| Host | GitHub Pages (free), user site at `https://dan-tsu.github.io` |
| Deploy | `.github/workflows/deploy.yml` — bun build → Pages, on push to `main` |
| Content | Markdown/MDX in `src/content/blog/` with frontmatter |
| Cost | €0 recurring. Custom domain optional later (~€12/yr registration only) |

## The publish loop (how Max manages it)

1. You hand me a draft (Obsidian markdown, or we write it via the _PUBLISH skill).
2. I add `src/content/blog/<slug>.md` with frontmatter (`title`, `description`, `pubDate`).
3. I `git commit` + `git push` to `main`.
4. GitHub Actions builds and deploys — live in ~60s.
5. I verify the live page with Interceptor before telling you it's up.

## Local preview

```bash
cd ~/Projects/dan-tsu.github.io
bun run dev      # http://localhost:4321
bun run build    # production build into ./dist
bun run preview  # serve the built site
```

## Going live (when you're ready — one-time)

1. Create a **public** repo on GitHub named exactly `dan-tsu.github.io`.
2. `git remote add origin git@github.com:dan-tsu/dan-tsu.github.io.git`
3. `git push -u origin main`
4. GitHub → repo **Settings → Pages → Source: GitHub Actions**.
5. The workflow runs; site appears at `https://dan-tsu.github.io`.

## Before the first publish

- Replace the example posts in `src/content/blog/` (`first-post`, `second-post`,
  `third-post`, `markdown-style-guide`, `using-mdx`) — they're template filler.
- Set `SITE_TITLE` / `SITE_DESCRIPTION` in `src/consts.ts` (currently placeholders).
- Update `src/pages/about.astro` and the social links in `src/components/Header.astro`.

## Custom domain later (no rebuild)

Add a `public/CNAME` file containing the domain, set `site:` in `astro.config.mjs`
to the new URL, and point DNS at GitHub Pages. That's the whole migration.
