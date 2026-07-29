# Brian DeSousa — Portfolio

A single-page portfolio for a data analyst / creative developer. Built with
[Astro](https://astro.build) + Tailwind v4. Mostly-monochrome editorial design
with a generative scatter-plot hero and a "projects as a dataset" work index.

**Design concept — “Field Notes.”** The aesthetic system is the analyst’s own
materials: coordinate grids, plotted points, monospace numerals, and tabular
data. One restrained signal accent (electric cobalt `#2438FF`) marks live and
interactive elements.

## Commands

```bash
npm install        # install dependencies
npm run dev        # start dev server → http://localhost:4321
npm run build      # production build → ./dist (static)
npm run preview    # preview the production build
```

> If `npm install` fails with an `EACCES` cache error, your npm cache has
> root-owned files. Either run `sudo chown -R $(id -u):$(id -g) ~/.npm`, or
> install with a local cache: `npm install --cache ./.npm-cache`.

## Deploy

The site deploys automatically to GitHub Pages when changes are pushed to
`main`. The production URL is `https://www.briandesousa.me`.

In the repository's **Settings → Pages**, set **Source** to **GitHub Actions**.
The workflow in `.github/workflows/deploy.yml` installs dependencies, builds the
static Astro site, and publishes `dist/`.

## Replace the placeholder content

All copy is written to be realistic but is placeholder — swap in the real thing:

| What | Where |
| --- | --- |
| Name, bio, disciplines, hero copy | `src/components/Hero.astro`, `src/components/Profile.astro` |
| Projects (title, blurb, tags, metric) | `projects` array in `src/components/Work.astro` |
| Skills & stats | `disciplines` / `stats` arrays in `src/components/Practice.astro` |
| Email & social links | `socials` array in `src/components/Contact.astro` |
| Location / coordinates | `src/components/Nav.astro`, `src/components/Contact.astro` |
| Portrait image | replace the `.profile__portrait` placeholder in `src/components/Profile.astro` with an `<img>` |
| Project thumbnails | the CSS `.work__thumb--*` motifs in `src/components/Work.astro`, or swap for real images |

## Notes on motion & performance

- The hero scatter field is vanilla canvas: capped point count, DPR-aware,
  pointer-reactive, autonomous while idle, and paused when off-screen.
- Everything respects `prefers-reduced-motion` (renders the static final state).
- Hidden-then-reveal states are gated behind a `.js` class, so if scripts never
  run, **all content stays visible**.
- Append `?static` to the URL to force the non-animated static render.
- Fonts are self-hosted (Archivo, Hanken Grotesk, IBM Plex Mono) — no external
  requests, no layout shift.
