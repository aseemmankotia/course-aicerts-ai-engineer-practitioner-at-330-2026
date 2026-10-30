## Chapter 2 Cheat Sheet: Modern AI System Architecture

### Three-Layer Reference Architecture
| Layer | Responsibilities | Key Components |
|---|---|---|
| Data Layer | Ingestion, storage, feature computation | Ingestion pipelines, data lake/warehouse, **feature store** |
| Model Layer | Training, versioning, lineage | Training pipeline, **model registry** |
| Serving Layer | Exposing models for predictions | Inference API, batch/real-time serving infra |
| Feedback Loop | Monitor + improve | Prediction logs, drift monitors, retraining triggers |

### Batch vs Real-Time Inference
| Factor | Batch Inference | Real-Time Inference |
|---|---|---|
| Latency | Minutes–hours | Milliseconds–seconds |
| Cost | Lower (scheduled runs) | Higher (always-on infra) |
| Data freshness need | Low–medium | High |
| Scaling pattern | Fixed/scheduled compute | Autoscaling load balancer |
| Best for | Recommendations, reports, nightly scoring | Fraud detection, bidding, chat responses |

### Feature Store vs Model Registry (exam trap)
- **Feature Store** → lives in Data Layer → prevents training/serving skew by sharing feature logic.
- **Model Registry** → lives in Model Layer → tracks model versions, lineage, promotion stage.
- Do NOT swap these — frequently tested distractor pair.

### Feedback Loop Design — Required Components
1. Log every prediction + context
2. Capture ground truth / actual outcome
3. Monitor drift (input distribution) and decay (output quality) against a threshold
4. Automated retraining trigger tied to monitored signal — NOT solely a calendar schedule

### Scalability by Layer
| Layer | Scaling Lever |
|---|---|
| Data Layer | Partitioning, distributed storage, ingestion throughput |
| Model Layer | Parallelized/distributed training jobs |
| Serving Layer | Autoscaling API replicas behind load balancer |

### Common Exam Gotchas
- 5xx serving errors ≠ model drift (infra issue vs data/quality issue)
- Batch inference cannot satisfy sub-second, per-request latency requirements
- Fixed peak-sized provisioning wastes cost — prefer autoscaling
- Feature schema versioning prevents skew but does NOT detect live drift (monitoring does)
- Model layer ≠ Serving layer: training/versioning vs exposing inference APIs
