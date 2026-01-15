# One pager: Architecture decisions

## What this project is

A Kubernetes first, monorepo based reference implementation of a job processing platform.
Designed to evolve in stages from MVP to production grade capabilities.

## Naming

Repository: k8s monorepo job processing

## Core architecture principles

1. Kubernetes first architecture
2. Monorepo with clear boundaries
3. Contracts first communication using Proto
4. GitOps based delivery
5. Incremental evolution, no upfront overengineering

## Monorepo and tooling

1. Monorepo orchestrator: Nx
2. Package manager: pnpm
3. Language: TypeScript for API and Worker

## API and Worker runtime

1. API framework: Fastify
2. Default worker model: long running worker deployments
3. Autoscaling: KEDA later, based on queue lag and external metrics

## Job execution modes

1. Default mode: pooled workers (Deployment)
2. Special mode: ephemeral Kubernetes Jobs for
   a. heavy tasks
   b. fan out workloads split into subtasks
   c. isolation requirements

## Contracts

1. Proto is the source of truth
2. Versioning via package namespace, example: jobprocessing.v1
3. Buf lint from day one
4. Buf breaking check after a baseline exists

## Local development

1. docker compose for local dependencies
2. make dev as the primary entry point
3. local Kubernetes (kind or k3d) as a later stage, not required initially

## Observability

1. Logging
   a. structured JSON logs to stdout
   b. centralized logging later via Grafana Loki
   c. correlation fields: requestId and jobId
2. Metrics
   a. Prometheus compatible metrics
   b. exposed via a metrics endpoint
3. Future: OpenTelemetry for unified instrumentation

## Data and messaging roadmap

Planned incremental additions

1. Redis first (idempotency, locks, caching, optional queue)
2. PostgreSQL for authoritative job state storage
3. Kafka for event driven processing and worker scaling signals
4. MongoDB only if document style result storage is valuable

## Testing strategy

Layers introduced early as a skeleton

1. Unit tests
2. Contract tests based on Proto
3. Integration tests using docker compose
4. Minimal end to end tests
5. Load testing later using k6
6. Coverage checks enabled early

## Delivery strategy

1. Image tagging: immutable tags by git sha
2. GitOps: CI commits Helm values updates
3. Argo CD applies changes from Git

## Deferred topics

1. Security hardening and policy enforcement will be decided later
