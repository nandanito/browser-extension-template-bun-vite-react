# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

A boilerplate template for building Manifest V3 browser (Chrome) extensions with Bun, Vite 8, React 19, and TypeScript 6. Uses the `@crxjs/vite-plugin` (2.x stable) to generate the extension manifest and wire up all the extension surfaces.

## Commands

- `bun install` — install dependencies
- `bun run dev` — start Vite dev server with HMR (`vite --force`); output is served/written for loading as an unpacked extension
- `bun run build` — type-check (`tsc`, no-emit) then build with Vite into `dist/`
- `bun run lint` — ESLint (flat config, `eslint.config.js`), fails on any warning (`--max-warnings 0`)
- `bun run fmt` — Prettier-format all `tsx,ts,json,css,scss,md` files
- `bun run preview` — preview the production build

There is no test runner configured.

### Loading the extension
After `bun run dev` or `bun run build`, go to `chrome://extensions`, enable Developer Mode, click "Load unpacked", and select the `dist` folder.

## Architecture

**`src/manifest.ts` is the single source of truth for the extension.** It calls `defineManifest(...)` and pulls `name`, `description`, and `version` from `package.json`. `vite.config.ts` feeds this manifest into the `crx()` plugin, which generates `dist/manifest.json` and bundles every entry point referenced by the manifest. To add/remove an extension surface, permission, or icon, edit `src/manifest.ts` — do not hand-write a `manifest.json`.

**Entry points are root-level HTML files, each loading a `src/<surface>/index.tsx`.** The pattern is consistent across surfaces:
- Root HTML (`popup.html`, `options.html`, `newtab.html`, `sidepanel.html`, `devtools.html`) → `<script src="/src/<surface>/index.tsx">`
- `src/<surface>/index.tsx` mounts the React root → renders `<Surface />` component (e.g. `Popup.tsx`, `Options.tsx`)

Surfaces present: `popup`, `options`, `newtab` (overrides Chrome's new tab via `chrome_url_overrides`), `sidepanel`, `devtools`, plus non-React scripts `background/index.ts` (service worker, `type: module`) and `contentScript/index.ts` (injected into all http/https pages).

**Static assets:** `public/` is copied verbatim to the build root. Manifest icons reference `img/logo-*.png` (served from `public/img/`).

## Notes / gotchas

- Styling is plain CSS (per-surface `.css` files) — there is no Tailwind/CSS framework configured.
- Adding a new React surface requires three coordinated changes: a root `.html` file, a `src/<surface>/` directory with `index.tsx`, and an entry in `src/manifest.ts`.
- There is a single `tsconfig.json` (no project references / composite split). It `include`s both `src` and `vite.config.ts` and is no-emit — type-checking only; Vite/Rolldown does the actual bundling.
- `@types/chrome` is loaded via `compilerOptions.types: ["chrome"]` — it must stay inside `compilerOptions` (a top-level `types` key is silently ignored).
- Firefox support is listed as WIP; the manifest and tooling target Chrome.
