# Contributing

Thanks for your interest in improving this template! Contributions of all
kinds are welcome — bug fixes, new extension surfaces, docs, and ideas.

## Prerequisites

- [Bun](https://bun.sh/) (the repo is pinned to a Bun lockfile — please use Bun, not npm/yarn/pnpm)
- A Chromium-based browser for testing (see the README for Firefox notes)

## Getting started

```sh
bun install
bun run dev
```

Then load the generated `dist` folder as an unpacked extension (see the
[README](./README.md#getting-started) for browser-specific steps).

## Project layout

- `src/manifest.ts` is the **single source of truth** for the extension manifest
  (name/description/version come from `package.json`). Add or change permissions,
  icons, and surfaces here — never hand-edit a generated `manifest.json`.
- Each extension surface is a root `*.html` entry that loads `src/<surface>/index.tsx`.
  Adding a surface means three coordinated changes: the HTML file, the
  `src/<surface>/` directory, and an entry in `src/manifest.ts`.

See [`CLAUDE.md`](./CLAUDE.md) for a deeper architecture overview.

## Before opening a pull request

Please make sure the following pass locally — CI runs the same checks:

```sh
bun run lint    # ESLint (flat config), zero warnings allowed
bun run build   # tsc type-check + Vite production build
bun run fmt     # Prettier formatting
```

## Pull request guidelines

- Branch off `main` and keep PRs focused on a single concern.
- Reference any related issue (e.g. `Closes #123`).
- Update the README/docs when you change behavior or add a surface.
- Keep the template **minimal** — it's a starting point, so prefer small,
  illustrative examples over heavy abstractions or extra dependencies.

## Reporting bugs / requesting features

Open an issue with clear reproduction steps (for bugs) or a short rationale
(for features). Check the existing [open issues](https://github.com/nandanito/browser-extension-template-bun-vite-react/issues)
first to avoid duplicates.
