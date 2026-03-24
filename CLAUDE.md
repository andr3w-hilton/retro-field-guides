# retro-field-guides

Personal retro game field guides. Single-page HTML files, hosted on GitHub Pages, installable as a PWA.

**Live URL:** https://andr3w-hilton.github.io/retro-field-guides/
**Repo:** github.com/andr3w-hilton/retro-field-guides
**Branch:** master - push directly, Pages auto-deploys (~60s build time)

## Structure

```
/index.html                  - hub page (lists all guides)
/manifest.json               - PWA manifest
/sw.js                       - service worker (cache-first, offline support)
/icons/                      - SVG icons (192 + 512)
/{game-slug}/index.html      - one folder per guide
```

## Adding a new guide

1. Create `/{game-slug}/index.html` - copy an existing guide as a template
2. Add a card to `index.html` in the guides grid
3. Push - that's it

## Critical: GitHub Pages path rules

This is a **project site** served from `/retro-field-guides/`, not `/`.
All internal hrefs and asset references must use the full path prefix:

- Links: `href="/retro-field-guides/{game-slug}/"`
- Manifest: `href="/retro-field-guides/manifest.json"`
- SW registration: `register('/retro-field-guides/sw.js')`
- Icons: `/retro-field-guides/icons/icon-192.svg`

**Do not use bare absolute paths** like `/links-awakening/` - they will 404.
Relative paths (e.g. `../manifest.json`) are a safe alternative within subfolders.

When adding a new guide, also add its URLs to the `PRECACHE` array in `sw.js` and bump the cache version (`field-guides-v2`, etc.) so the SW picks up the new content.

## Design system

Game Boy green palette - keep all guides consistent with this:

```css
--gb-darkest: #0f1a0f    /* page background */
--gb-screen-bg: #9bbc0f  /* main screen colour */
--gb-screen-dark: #0f380f
--gb-screen-shadow: #306230
--gb-lightest: #c8e870
```

Fonts: VT323 (headings/pixel text), Share Tech Mono (body) - both from Google Fonts.

Visual effects: scanline overlay (body::before), pixel noise (body::after), clipped corners on .screen-wrapper.

## Current guides

| Slug | Game | Status |
|------|------|--------|
| links-awakening | The Legend of Zelda: Link's Awakening (GB, 1993) | Active playthrough |
| super-mario-land | Super Mario Land (GB, 1989) | Active playthrough |
| pokettohiro | Pokettohiro (GBC, 2024) | Active playthrough |
