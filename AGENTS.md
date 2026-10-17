# AGENTS.md

This file is the onboarding guide for AI coding agents working in this repository.

## Project overview

This repository is the source for the GitHub Pages **user site** `erbaoyihao.github.io`
(remote: `https://github.com/erbaoyihao/erbaoyihao.github.io`). The site's content is
served directly from the `main` branch at `https://erbaoyihao.github.io`.

**Current state:** the repository was just initialized (single commit "Initial commit")
and contains only a one-line `README.md` with the repository name. There is **no source
code, no build system, and no site content yet** — the actual site has not been created.

## Repository layout

```
.
├── .git/
├── README.md      # One line: "# erbaoyihao.github.io"
└── AGENTS.md      # This file
```

## Technology stack

None is established yet. GitHub Pages supports two broad options; whichever the author
chooses will define the stack and should be documented here when introduced:

- **Plain static files** — commit `index.html`, CSS, and JS directly at the repository
  root; GitHub Pages serves them as-is with no build step.
- **Jekyll** (GitHub Pages' default static site generator) — a `_config.yml` and
  Markdown/liquid content that GitHub builds automatically on push. A plain `Gemfile`
  or `_config.yml` in the root will indicate this choice.
- An externally built site (e.g. Hugo, Next.js, Astro) would require a build command
  and usually a GitHub Actions workflow — none exists today.

## Build and test commands

There are currently **no build, test, lint, or CI commands** — no `package.json`,
`Gemfile`, `_config.yml`, or GitHub Actions workflow exists. When a stack is added,
record the exact commands here (e.g. how to serve the site locally and how to verify
changes before pushing).

## Deployment

- Deployment is automatic: GitHub Pages publishes whatever is on the `main` branch
  (repository root) to `https://erbaoyihao.github.io` after each push.
- There is no staging environment; pushing to `main` makes changes live immediately.
  Verify changes locally before pushing, and prefer pull requests or at least a local
  preview for non-trivial changes.

## Development conventions

- Git default branch: `main`.
- No code style, commit-message convention, or review process is established yet.
- Keep this `AGENTS.md` up to date as content and tooling are added — it is currently
  the only authoritative description of the project.

## Security considerations

- This is a public repository (GitHub Pages user sites must be public unless the
  account has a paid plan): never commit secrets, API keys, or personal data.
- Everything committed to `main` is publicly served — treat the whole tree as public.
