# React + Vite Template

A minimal, modern, opinionated React foundation. It gives you a small, working baseline — React 19, Vite 8, strict TypeScript, Tailwind CSS v4, Vitest, and Oxc tooling — without imposing architecture on your app.

## 💡 Why this template?

- **Small by design.** The baseline contains only what every project needs to run, test, and build. Everything else is yours to add when (and if) your app needs it.
- **Opinionated defaults.** Strict TypeScript, type-aware linting, reproducible toolchain versions locked by the committed `pnpm-lock.yaml`, and a single `pnpm check` command that covers lint, format, types, tests, and dead-code detection — with `pnpm check:ci` adding the coverage gate to match what CI runs.
- **Fast tooling.** The Oxc toolchain (oxlint + oxfmt) replaces the slower ESLint + Prettier setup, and Vite provides instant dev-server startup.
- **Easy to adopt.** Fork it, rename it, replace `src/App.tsx`, and start building.

## ✨ Features

- React 19 with `React.StrictMode`
- Vite 8 dev server and optimized production builds
- Strict TypeScript with a solution-style tsconfig (app + node projects)
- Tailwind CSS v4 via the `@tailwindcss/vite` plugin (CSS-first, no `tailwind.config.js`)
- Unit tests with Vitest, happy-dom, and Testing Library (plus jest-dom matchers)
- oxlint (type-aware) for linting and oxfmt for formatting
- knip to detect unused files, exports, and dependencies
- `@` path alias mapped to `src/` (Vite + tsconfig)
- pnpm with Node 24.x support and pnpm 12.8.2 pinned (`engines` + `engine-strict`)
- GitHub Actions CI running lint, format check, types, tests (with enforced coverage), dead-code detection (knip), and a production build as a single job

## 🛠 Tech stack

| Technology                | Purpose                           |
| ------------------------- | --------------------------------- |
| React / react-dom         | UI library                        |
| Vite                      | Dev server and build tool         |
| TypeScript                | Type safety (`strict: true`)      |
| Tailwind CSS              | Styling                           |
| Vitest                    | Unit testing                      |
| happy-dom                 | Browser environment for tests     |
| @testing-library/react    | Component testing helpers         |
| @testing-library/jest-dom | DOM matchers for Vitest           |
| oxlint                    | Linting (type-aware)              |
| oxfmt                     | Code formatting                   |
| knip                      | Unused files/exports/dependencies |
| pnpm                      | Package manager                   |
| Node.js                   | Runtime                           |

Exact installed versions are locked in `pnpm-lock.yaml`; the semver ranges in `package.json` allow compatible updates.

## ✅ What's included?

- A working starter app: `src/main.tsx`, `src/App.tsx`, `src/index.css`
- A passing sample test (`src/App.test.tsx`) and Vitest setup (`src/test/setup.ts`)
- Build/test config: `vite.config.ts`, `vitest.config.ts`, solution-style `tsconfig.json` (references `tsconfig.app.json` + `tsconfig.node.json`)
- Tooling config: `.oxlintrc.json`, `.oxfmtrc.json`, `knip.json`
- Environment pinning: `.nvmrc`, `.npmrc` (`engine-strict=true`), `packageManager` field
- GitHub Actions workflow (`.github/workflows/ci.yml`) and Dependabot config (`.github/dependabot.yml`)
- Editor and editor experience: `.editorconfig`, `.vscode/settings.json`, `.vscode/extensions.json` (recommended: Tailwind CSS IntelliSense, Vitest, EditorConfig, Oxc)
- `LICENSE` (MIT) and a `public/` folder with `favicon.svg`

## 🚫 What's intentionally not included?

The template deliberately does **not** include:

- **React Router** — no client-side routing
- **Redux / Zustand** — no state-management library
- **TanStack Query** — no server-state / data-fetching cache
- **Axios** — no HTTP client (native `fetch` is available)
- **Storybook** — no component workshop
- **Playwright** — no end-to-end test setup
- **UI framework** — no component library (plain Tailwind CSS only)
- **Authentication** — no auth or session handling
- **Backend** — no API, database, or server code

These are deliberately omitted to keep the foundation small. A minimal baseline is easier to understand, audit, and customize — and every one of the above can be added later with `pnpm add` once your application actually needs it.

## 🚀 Getting started

Prerequisites:

- Node.js **24.x** (any Node 24; major version pinned in `.nvmrc` and `engines.node`)
- pnpm **12.8.2** (pinned via `packageManager` in `package.json`)

Corepack is bundled with Node.js 24 but disabled by default (since Node 23). Enable it to get the pinned pnpm version automatically:

```bash
corepack enable
pnpm install
pnpm run dev
```

If you would rather not use Corepack, install the pinned pnpm version directly instead: `npm install -g pnpm@12.8.2`.

The dev server is available at `http://localhost:5173`.

Notes:

- `engines` + `.npmrc` (`engine-strict=true`) make pnpm fail fast on a Node/pnpm version mismatch.
- Install `node_modules` on the OS where you run the project — platform-specific native binaries (oxlint, oxfmt, esbuild) are not portable between Windows, WSL, and Linux. If you switch OS, delete `node_modules` and run `pnpm install` again.

## 📦 Why pnpm?

This template uses pnpm instead of npm for three reasons:

- **Fast, disk-efficient installs** — pnpm keeps packages in a global content-addressable store and hard-links them into `node_modules`, so installs are quick even when projects share dependencies.
- **Strict dependency model** — only explicitly declared dependencies are reachable from your code, which prevents silently relying on transitive ("phantom") packages.
- **Consistency** — the pnpm version is pinned via the `packageManager` field in `package.json` (picked up automatically by Corepack) and `engines`, so local development and CI always use the same version.

This template uses pnpm 12.8.2 and the repository is tested with pnpm. Switching to a different package manager is up to you, but pnpm is the supported one.

## ⌨️ Available commands

| Command                  | Description                                                                                                                  |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------- |
| `pnpm run dev`           | Start the Vite dev server                                                                                                    |
| `pnpm run build`         | Build for production into `dist/`                                                                                            |
| `pnpm run preview`       | Serve the production build locally                                                                                           |
| `pnpm run check`         | Run lint, format check, typecheck, tests, and knip                                                                           |
| `pnpm run check:ci`      | Full quality gate with coverage (lint, format, types, tests with coverage, knip) — matches what CI runs                      |
| `pnpm run lint`          | Lint all project TypeScript files with oxlint (`src/` + config files; `node_modules`/`dist` ignored)                         |
| `pnpm run lint:fix`      | Lint all project TypeScript files with oxlint and auto-fix                                                                   |
| `pnpm run format`        | Format all project files with oxfmt (`node_modules`/`dist` ignored)                                                          |
| `pnpm run format:check`  | Fail on files that need formatting                                                                                           |
| `pnpm run typecheck`     | Type-check all projects with `tsc -b`                                                                                        |
| `pnpm run test`          | Run the test suite with Vitest                                                                                               |
| `pnpm run test:coverage` | Run the test suite with coverage (`@vitest/coverage-v8`); fails if coverage falls below the thresholds in `vitest.config.ts` |
| `pnpm run fix`           | `lint:fix` followed by `format`                                                                                              |
| `pnpm run knip`          | Detect unused files, exports, and dependencies                                                                               |

## 🧪 Testing

- **Vitest** runs in the **happy-dom** environment (chosen for speed over `jsdom`; if a library needs richer browser behavior — e.g. certain media or canvas APIs — switch to `jsdom` with `pnpm add -D jsdom` and `environment: "jsdom"` in `vitest.config.ts`)
- **@testing-library/react** for rendering and querying components
- **@testing-library/jest-dom** adds DOM matchers (loaded via `src/test/setup.ts`, which also runs `cleanup` after each test)
- Coverage is enforced with `pnpm run test:coverage` — minimum thresholds (statements, branches, functions, lines) are set in `vitest.config.ts` and the run fails when they are not met

```bash
pnpm run test
```

`src/App.test.tsx` contains a sample test you can use as a starting point.

## 🔍 Code quality

The template uses the **Oxc** toolchain instead of ESLint + Prettier:

- **oxlint** — type-aware linting with the `unicorn`, `typescript`, `oxc`, `react`, `jsx-a11y`, and `vitest` plugins (see `.oxlintrc.json`)
- **oxfmt** — code formatting (see `.oxfmtrc.json`)
- **knip** — detects unused files, exports, dependencies, and devDependencies

Both `knip.json` and `.oxfmtrc.json` are intentionally empty — knip and oxfmt run with their sensible defaults.

TypeScript runs in `strict` mode with additional strictness flags in the solution: `noUnusedLocals` and `noUnusedParameters` in `tsconfig.base.json`, plus `noUncheckedIndexedAccess`, `exactOptionalPropertyTypes`, `noImplicitOverride`, `noImplicitReturns`, and `noFallthroughCasesInSwitch` in `tsconfig.app.json`.

Run all at once:

```bash
pnpm run check        # fast gate (no coverage): lint, format, types, tests, knip
pnpm run check:ci     # full gate with coverage — matches what CI runs
```

## 📁 Project structure

```
.
├── .github/
│   └── workflows/
│       └── ci.yml             # GitHub Actions: single job running the CI check + build
├── public/
│   └── favicon.svg            # Static assets
├── src/
│   ├── test/
│   │   └── setup.ts           # Vitest setup (jest-dom matchers, cleanup)
│   ├── App.test.tsx           # Sample test
│   ├── App.tsx                # Starter app
│   ├── index.css              # Tailwind entry point
│   └── main.tsx               # React entry (StrictMode)
├── index.html                 # HTML shell (title/description are placeholders)
├── knip.json                  # knip configuration
├── tsconfig.json              # Solution-style root (app + node references)
├── tsconfig.app.json          # App code (strict, `@/*` paths)
├── tsconfig.base.json         # Shared compiler options
├── tsconfig.node.json         # Config files (vite.config.ts, vitest.config.ts)
├── vite.config.ts             # React + Tailwind plugins, `@` alias
└── vitest.config.ts           # Merges vite.config.ts, happy-dom + setup file
```

The `@` alias points to `src/` (configured in `vite.config.ts` and `tsconfig.app.json`):

```ts
import { App } from "@/App";
```

Organize `src/` however your app needs — the template only requires that entry and test files stay where the config expects them.

## 🎨 Customizing the template

1. Rename the package (`name` in `package.json`) and update the title/description in `index.html`.
2. Replace `src/App.tsx` with your application.
3. Add libraries with `pnpm add <package>` when your app needs them (routing, state management, data fetching, UI, E2E, etc.).
4. Keep `pnpm check` green locally and `pnpm check:ci` green before pushing (this is what CI runs).

## 🔄 Updating dependencies

- `pnpm update` — update dependencies within their semver ranges
- `pnpm update --latest` — jump to the latest major versions, then review breaking changes
- Dependabot handles **minor/patch** updates weekly and security patches daily (`.github/dependabot.yml`); major versions are bumped by hand in `chore/` branches
- The Node.js major version (24.x) and the pnpm version are pinned in `engines`, `.nvmrc`, and the `packageManager` field. To change them, update all three together; Corepack will pick up the new pnpm version from `packageManager`.

## 📄 License

MIT — see [LICENSE](LICENSE). Use this template freely for personal or commercial projects.
