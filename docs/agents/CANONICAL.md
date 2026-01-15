# Agent Canonical Rules

This file is the single source of truth for all AI agents working in this repository.
All agent specific instructions must reference this file and must not duplicate it.

## Project identity

Repository: k8s monorepo job processing  
Goal: a Kubernetes first reference implementation of a job processing platform that evolves in stages.

## Engineering decisions summary

1. Monorepo orchestrator: Nx
2. Package manager: pnpm
3. Language: TypeScript for API and worker
4. API framework: Fastify
5. Contracts: Proto as source of truth, versioning via package namespace (example: jobprocessing.v1)
6. GitOps: CI commits Helm values image tag updates, Argo CD applies from Git
7. Logging: structured JSON to stdout, centralized logging later via Grafana Loki
8. Metrics: Prometheus compatible metrics, Grafana dashboards later
9. Autoscaling: long running worker deployments by default, KEDA later
10. Heavy tasks: ephemeral Kubernetes Jobs only for heavy or fan out workloads
11. Local dev: docker compose for dependencies plus make dev, local k8s later (kind or k3d)
12. Testing: layered approach from day one, include coverage checks

## Repository rules

1. Prefer small, reviewable changes.
2. Keep architecture and boundaries explicit. Apps must depend on libraries, not the other way around.
3. Contracts first. Do not introduce ad hoc payload shapes outside Proto.
4. Configuration is env first and validated at startup using Zod.
5. Logs must include correlation fields when available: requestId and jobId.
6. Code comments and technical documentation must be in English.
7. Do not introduce new tools unless there is a clear, documented reason and a minimal adoption plan.
8. Rule precedence:
   If a canonical rule conflicts with clarity, simplicity, or the correct evolution of the system,
   the rule may be intentionally broken.

   In such cases the agent MUST:

   - explain why the rule was broken
   - document the decision explicitly
   - prefer system correctness over procedural compliance

## Output expectations

1. Every change must include a concise explanation of what changed and why.
2. If a change adds or modifies commands, ensure they are documented in README or docs.
3. Provide commands to verify the change locally (lint, test, build, run).

## Quality gates

Before declaring work done, ensure:

1. Lint passes
2. Tests pass
3. Types compile
4. Commands referenced in docs actually exist

## Communication style

1. Be direct and precise.
2. Prefer structured output.
3. Avoid unnecessary verbosity.
4. When uncertain, state assumptions clearly.

## Security note

Security hardening and policy enforcement are deferred decisions.
Do not introduce broad security frameworks without explicit direction.
