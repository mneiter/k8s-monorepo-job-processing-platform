# Observability Strategy

## Logging
- Structured JSON logs to stdout
- Centralized logging via Grafana Loki (added later)
- Correlation via requestId and jobId

## Metrics
- Prometheus-compatible metrics
- Exposed via /metrics endpoint

## Future Evolution
- OpenTelemetry for unified instrumentation
- Distributed tracing added before Kafka adoption
