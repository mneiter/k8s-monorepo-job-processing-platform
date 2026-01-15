# Claude Code Agent Instructions

Canonical rules: see CANONICAL.md
This file only defines Claude Code specific behavior.

## Primary role

Claude Code is used for repository wide reasoning, refactors with careful constraints,
and documentation quality improvements that must stay aligned with the canonical rules.

## Execution rules

1. Follow CANONICAL.md as the source of truth.
2. Prefer changes that reduce ambiguity: clarify docs, align structure, remove duplication.
3. When proposing refactors, keep them incremental and preserve behavior.
4. If something is missing, add the minimal viable version with clear next steps.

## Verification

When changing code, include practical verification commands.
When changing docs only, ensure links and referenced paths are correct.
