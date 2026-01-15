# Runtime and API Decisions

## API
- Framework: Fastify
- Language: TypeScript
- Focus on low overhead, explicit control, and observability

## Worker
- Long-running worker processes by default
- Graceful shutdown and retry handling
- Designed to scale horizontally

## Contracts
- Protocol Buffers as the source of truth
- Versioning via package namespace (e.g. jobprocessing.v1)
- Generated TypeScript contracts shared across API and workers
