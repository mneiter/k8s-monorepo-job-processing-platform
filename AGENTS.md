# Agent entrypoint

This file is the entrypoint for all AI agents working in this repository.

Before making any changes, every agent MUST read and follow the canonical
agent rules defined in:

docs/agents/CANONICAL.md

This repository intentionally separates:

- canonical rules (shared by all agents)
- agent specific instructions
- architectural and engineering decisions

Agents must respect this structure and must not duplicate canonical rules.

---

## Available agents

### Codex

File:
docs/agents/CODEX.md

Purpose:
Codex is used primarily for implementation work:

- writing and modifying code
- adding files and folders
- producing PR ready changes
- updating configuration and build scripts

Codex MUST:

- keep diffs minimal and reviewable
- ensure commands referenced in code or docs actually exist
- include verification steps for non trivial changes

---

### Claude Code

File:
docs/agents/CLAUDE_CODE.md

Purpose:
Claude Code is used for:

- repository wide reasoning
- architectural refactors with constraints
- documentation structure and clarity
- alignment with canonical decisions

Claude Code MUST:

- preserve existing behavior when refactoring
- prefer incremental improvements
- avoid introducing new tools or abstractions without justification

---

## Decision authority

Canonical decisions are documented under:
docs/decisions/

Agents MUST:

- follow existing decisions
- not silently override them
- propose changes explicitly when a decision needs to evolve

If a decision is unclear or missing, the agent should:

1. make the minimal safe assumption
2. document it
3. mark it clearly as a proposal

---

## Scope discipline

Agents should not:

- introduce unrelated improvements
- refactor large areas without request
- add technologies not already discussed

The goal of this repository is not maximal feature coverage,
but a clear, production grade reference that evolves intentionally.

---

## Final note

When in doubt:

- prefer clarity over cleverness
- prefer explicit decisions over implicit behavior
- prefer evolution over reinvention
