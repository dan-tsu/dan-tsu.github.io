## Blog publishing rules

**Every blog post MUST ship with a hero image — no exceptions.** Publishing a post without a `heroImage` is not allowed; a heroless post breaks visual consistency with the rest of the index.

- Generate the hero via the **Art skill → Essay workflow** (`nano-banana-pro`, landscape `3:2`, no text in the image).
- **This blog's deviations from the Art skill defaults:** no "KAI" signature, and **no** `--thumbnail`/`--remove-bg` sepia wiring — this is a white-background Astro blog, so use a normal opaque `heroImage` jpg in `src/assets/`.
- Wire it as `heroImage: "../../assets/<slug>-hero.jpg"` in the post frontmatter (path relative to the `.md`).
- Verify the hero renders live with **Interceptor** (`eval --main`, not curl — see README "Verification gotchas") before considering the publish done.

See `README.md` → "Publish / update loop" and "Hero images (Art skill)" for the full procedure.

## Development

When starting the dev server, use background mode:

```
astro dev --background
```

Manage the background server with `astro dev stop`, `astro dev status`, and `astro dev logs`.

## Documentation

Full documentation: https://docs.astro.build

Consult these guides before working on related tasks:

- [Adding pages, dynamic routes, or middleware](https://docs.astro.build/en/guides/routing/)
- [Working with Astro components](https://docs.astro.build/en/basics/astro-components/)
- [Using React, Vue, Svelte, or other framework components](https://docs.astro.build/en/guides/framework-components/)
- [Adding or managing content](https://docs.astro.build/en/guides/content-collections/)
- [Adding styles or using Tailwind](https://docs.astro.build/en/guides/styling/)
- [Supporting multiple languages](https://docs.astro.build/en/guides/internationalization/)
