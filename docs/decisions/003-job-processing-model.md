# Job Processing Model

## Default Execution Mode
- Long-running worker deployments
- Autoscaling based on queue pressure (later via KEDA)

## Alternative Execution Mode
Ephemeral Kubernetes Jobs are used for:
- heavy or long-running jobs
- workloads requiring isolation
- fan-out / subtask execution models

This dual-mode approach allows balancing throughput and isolation.
