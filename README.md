# Brochure Site Starter

Astro 6 · Tailwind CSS v4 · DaisyUI 5 · deployed to Netlify.

This is a template repo, not a finished site. It has the plumbing wired up;
design and content come from filling in `STYLE-GUIDE.md` fresh for each
project that starts from this template.

## Starting a new site from this template
1. `npm install`
2. Open the project in Zed, run `claude` in the terminal panel.
3. Fill out `STYLE-GUIDE.md` together with Claude (see `CLAUDE.md` for how
   that conversation should go) — brand voice, colors, type, page list.
4. Ask Claude to translate the palette into the `@plugin "daisyui/theme"`
   block in `src/styles/global.css`, and the nav/footer info into
   `src/site-config.ts`.
5. `npm run dev` and build out the pages listed in `STYLE-GUIDE.md`'s site map.
6. `npm run build` as a sanity check, then connect the repo to Netlify
   (Add new site → Import from Git — it auto-detects `astro build` → `dist`,
   no adapter needed).

**`npm run build` is a real quality gate, not just a compile step.** It runs
`astro check` (fails on missing required props — e.g. a page that doesn't
pass `title`/`description` to `BaseLayout`) and `eslint .` (fails on
accessibility issues, including a missing `alt` on an image) before `astro
build` ever runs. The same command is what Netlify runs, so these fail the
deploy too, not just your local build. Run `npm run lint` or
`npm run typecheck` alone to check just one half while iterating.

Optional, recommended once per clone: install daisyUI's official skill so
Claude uses current v5 class names instead of guessing from memory:
```
npx skills add saadeghi/daisyui --agent claude-code --yes
```

## What's here

| Path | Purpose |
|---|---|
| `CLAUDE.md` | Project memory for Claude Code — fill in per site |
| `STYLE-GUIDE.md` | The design/content brief — fill in per site |
| `src/site-config.ts` | Nav items, brand name, footer contact info — one source of truth |
| `src/styles/global.css` | DaisyUI theme tokens + font mapping — the main thing that changes per site |
| `astro.config.mjs` | Tailwind v4 Vite plugin, static output, Fonts API, sitemap integration |
| `eslint.config.js` | Accessibility rules (incl. image alt text) as build-breaking errors |
| `public/robots.txt` | Points crawlers at the auto-generated sitemap — update the domain per site |
| `src/layouts/BaseLayout.astro` | Document shell: fonts, meta/SEO via astro-seo, Navbar/Footer wiring |
| `src/components/Navbar.astro` | Responsive nav with mobile dropdown, active-page state |
| `src/components/Hero.astro` | Flexible hero — text-only or split with an image slot |
| `src/components/Footer.astro` | Nav/contact/social columns + copyright strip |
| `src/env.d.ts` | Astro's ambient type reference — required for `astro:assets`/`astro:content` etc. to resolve in your editor |
| `src/pages/index.astro` | Placeholder home page so the project builds out of the box |

## Commands
| Command | What it does |
|---|---|
| `npm run dev` | Local dev server |
| `npm run build` | `astro check` + `eslint .` + production build — fails on missing props or a11y errors |
| `npm run lint` | Just the accessibility/lint check |
| `npm run typecheck` | Just the `astro check` type/prop validation |
| `npm run preview` | Preview the production build locally |
