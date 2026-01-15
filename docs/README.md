# Architecture & Engineering Decisions

This directory documents the architectural and engineering decisions behind the
`k8s-monorepo-job-processing` project.

The goal of this documentation is to:

- make decisions explicit,
- explain _why_ choices were made,
- preserve architectural context over time,
- allow intentional evolution without losing rationale.

Documents in this directory are expected to evolve as the platform grows.

---

## Entry points

### Decision summary

For a high level overview of all decisions, start here:

- decisions/000-decisions-summary.md

### Detailed decisions

All detailed architectural and engineering decisions are documented under:

- decisions/

Each document focuses on a specific area (architecture, tooling, runtime, observability, testing, etc.).

---

## Agent instructions

This repository is designed to be worked on by multiple AI agents.

All agents MUST follow the canonical agent rules defined in:

- agents/CANONICAL.md

Agent specific instructions are located under:

- agents/

Before making changes, agents should start from:

- AGENTS.md (repository root)

---

## How to use this documentation

- Read the decision summary first.
- Dive into individual decision documents as needed.
- When a decision evolves, update the relevant document instead of creating hidden assumptions.
- Keep documentation aligned with the actual state of the repository.
