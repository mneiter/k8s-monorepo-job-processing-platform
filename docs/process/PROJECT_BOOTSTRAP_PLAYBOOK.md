# Project Bootstrap Playbook

This document describes the step by step process used to design, plan,
and bootstrap a new repository before implementation begins.

The goal of this playbook is reproducibility.
It captures not tools, but the sequence of decisions and artifacts
that reduce future cost of change.

This process is intentionally lightweight but disciplined.
It is designed for production grade systems and reference projects.

---

## Operating mode

1. Decisions before code
2. Explicit over implicit
3. Evolution over upfront completeness
4. Documentation as part of the system

If a decision affects repository structure, CI/CD, contracts,
or observability, it is documented before implementation.

---

## Step 1. Define the project goal

Clarify the project in a single sentence.

Key questions:

- Is this a product, a reference implementation, or an internal platform?
- Who is the primary reader six months from now?
- What qualities matter most: stability, clarity, scalability, or learning?

Artifact:

- docs/decisions/000-architecture-overview.md

---

## Step 2. Choose the repository name

The repository name should describe:

- the primary platform (for example k8s)
- the architectural style (for example monorepo)
- the problem domain (for example job processing)

Avoid marketing terms or abstract names.

Artifact:

- repository name
- referenced in docs/decisions/000-decisions-summary.md

---

## Step 3. Lock high cost decisions

Identify decisions that are expensive to change later.

Typical examples:

- monorepo strategy and tooling
- primary language choices
- contract format and versioning
- delivery model (GitOps, CI responsibilities)
- worker execution model
- observability strategy

Artifacts:

- docs/decisions/001-monorepo-and-tooling.md
- docs/decisions/002-runtime-and-api.md
- docs/decisions/003-job-processing-model.md
- docs/decisions/004-observability.md

---

## Step 4. Separate now vs later

Avoid pulling the full technology stack into the initial implementation.
Instead, define an explicit evolution path.

Plan which components are added incrementally, for example:

- Redis
- PostgreSQL
- Kafka
- Autoscaling mechanisms
- Observability extensions
- Load testing
- Security hardening

Artifact:

- docs/decisions/007-future-roadmap.md

---

## Step 5. Define local development workflow

Choose a local setup that minimizes friction:

- docker compose for local dependencies
- a single entry command such as make dev
- local Kubernetes as a later, optional stage

Artifact:

- docs/decisions/005-local-development.md

---

## Step 6. Define testing strategy early

Testing is introduced as a structure from day one,
even if coverage is minimal initially.

Layers:

- unit tests
- contract tests
- integration tests
- minimal end to end tests
- load testing later

Quality gates:

- tests must exist early
- coverage checks enabled early

Artifact:

- docs/decisions/006-testing-strategy.md

---

## Step 7. Create a decisions summary

Provide a one page entry point summarizing all decisions.

Purpose:

- fast orientation
- shared mental model
- onboarding reference

Artifact:

- docs/decisions/000-decisions-summary.md

---

## Step 8. Establish agent discipline

If AI agents are used, treat them as team members.

Rules:

- one canonical rules file
- agent specific files reference the canonical rules
- no duplication of authority
- explicit decision ownership

Artifacts:

- docs/agents/CANONICAL.md
- docs/agents/CODEX.md
- docs/agents/CLAUDE_CODE.md
- AGENTS.md (repository root)

---

## Step 9. Documentation as navigation

Documentation must guide readers.

docs/README.md should clearly point to:

- decisions summary
- detailed decisions
- agent rules
- repository entry points

Artifact:

- docs/README.md

---

## Step 10. Begin implementation

Implementation starts only after:

1. architectural decisions are documented
2. a decisions summary exists
3. agent rules are in place
4. documentation structure is clear

At this point, Stage 0 implementation can begin.

---

## Reuse checklist

Use this checklist to bootstrap future projects:

1. Define project goal
2. Choose repository name
3. Lock high cost decisions
4. Separate now vs later
5. Define local development workflow
6. Define testing strategy
7. Create decisions summary
8. Establish agent discipline
9. Prepare documentation navigation
10. Start Stage 0 implementation

---

## Final note

This playbook is not rigid.
It is intended to minimize accidental complexity,
not to eliminate iteration.

If the process needs to evolve, evolve the playbook explicitly.
