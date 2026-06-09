# glue-coding-agent-site

Marketing homepage for the **glue coding agent** — the `glue` binary
from [`erain/glue`](https://github.com/erain/glue): an interactive
terminal coding agent (TUI + headless goal loop) that runs on Gemini,
a ChatGPT subscription (Codex), or open-weight models via OpenRouter
and NVIDIA.

Astro + Tailwind, statically generated, deployed via Vercel. Mirrors
the pattern established in
[`glue-framework-site`](https://github.com/erain/glue-framework-site)
and [`glue-review-site`](https://github.com/erain/glue-review-site) —
same design system, terminal-green accent.

## Dev

Requires Node 22+.

```sh
npm install
npm run dev      # http://localhost:4321
npm run build    # static output → ./dist/
npm run preview  # serve ./dist/ locally
```

## Layout

```
src/
  layouts/Base.astro       page shell (head, header, footer)
  components/Section.astro numbered-section block
  pages/index.astro        the single page — hero, 7 numbered sections, FAQ
  styles/global.css        Tailwind v4 + theme tokens (green accent)
public/favicon.svg         green terminal-prompt mark
```

The site is **one page on purpose** — the repo README's
[CLI section](https://github.com/erain/glue#the-glue-cli) is the
primary CTA.

## Content edits

All copy lives in [`src/pages/index.astro`](src/pages/index.astro).
Code snippets and the card grids are hoisted into JS template strings /
arrays at the top of the frontmatter so the markup stays scannable.

## Deploy

Vercel auto-detects Astro. To wire it up the first time:

1. Vercel dashboard → Add New → Project → Import `erain/glue-coding-agent-site`.
2. Framework preset: Astro (auto-detected).
3. Root directory: `./`. Build command: `npm run build`. Output: `dist/`.
4. Deploy.

Every push to `main` auto-deploys. PRs get preview URLs.

Set `ASTRO_SITE` at deploy time if a custom domain lands. The default
`astro.config.mjs` site is `https://glue-coding-agent-site.vercel.app`.

## OG image

`public/og.png` is the 1200×630 social-share image referenced by
`Base.astro`. Regenerate from [`scripts/og.html`](scripts/og.html):
open it in a browser at 1200×630 viewport, screenshot, save to
`public/og.png`.
