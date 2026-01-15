# Codex Agent Instructions

Canonical rules: see CANONICAL.md
This file only defines Codex specific behavior.

## Primary role

Codex is used for implementation work.
Focus on editing files, adding code, and producing PR ready diffs.

## Execution rules

1. Follow CANONICAL.md as the source of truth.
2. Prefer minimal diffs that are easy to review.
3. When adding new files, place them in the correct folder and update docs if needed.
4. Never invent commands. If a command is required, add it to package scripts, Nx targets, or Makefile.

## Verification

For any non trivial change, include a short verification section with commands such as:
pnpm lint
pnpm test
pnpm build
