# AGENT.md

Operating rules for AI agents working in this repository.

## Project

`react-vite-template` is a minimal, opinionated React + Vite starter template.

- **Stack** — React 19, Vite 8, strict TypeScript (solution-style tsconfig), Tailwind CSS v4, Vitest + happy-dom + Testing Library, Oxc tooling (oxlint + oxfmt), knip.
- **App code** — `src/` (`main.tsx`, `App.tsx`, `index.css`, `App.test.tsx`), with the `@/` alias mapped to `src/`.
- **Package manager** — pnpm 12.6.0, pinned via the `packageManager` field (picked up by Corepack) and `engines` + `engine-strict` in `.npmrc`.
- **Runtime** — Node.js 24.x (`.nvmrc` + `engines.node`).
- **Quality gates** — `pnpm check` (lint, format, types, tests, knip) and `pnpm check:ci` (same, plus coverage); CI runs `check:ci` + a production build.

See `README.md` for full documentation.

## Git workflow

**Rule: every change — no matter how small — happens on its own branch. `main` is only ever updated through a pull request, and only a human merges it.**

### Allowed

- Create a branch for every change, including one-line fixes.
- Commit to that branch (conventional commit messages; one logical change per commit).
- Push the branch to the remote (`git push -u origin <branch>`).
- Open a pull request for the branch (the human decides when and whether to merge).

### Forbidden

- **Never push to `main`** — no direct pushes, no force pushes, no pushing any ref to `main`.
- **Never merge** — no `git merge` into `main`, no merging pull requests (via GitHub, the `gh` CLI, or the API). Merging is done by the human, after review.
- **Never rewrite `main`** — no force pushes, resets, rebases, or branch deletions of `main`.

### Workflow

1. Start from the latest `main`: `git fetch origin`, then `git checkout -b <type>/<scope> main`.
2. Make the change and keep `pnpm check` green (run `pnpm check:ci` for dependency/config changes — that is what CI runs).
3. Commit with a conventional message (`chore:`, `fix:`, `feat:`, `docs:`, ...).
4. Push the branch and hand it to the human with the PR link. Do not merge.

### Branch naming

`<type>/<short-description>` — e.g., `chore/bump-pnpm-12.8.2`, `docs/add-agent-md`, `fix/vitest-setup`.
