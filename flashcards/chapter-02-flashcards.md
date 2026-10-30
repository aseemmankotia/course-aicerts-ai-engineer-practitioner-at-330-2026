## Chapter 2: The Architecture of Modern AI Systems — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | What are the three core layers in a modern AI system reference architecture? | Data layer, Model layer, Serving layer (wrapped by a Feedback loop). Exam tip: questions often test which layer 'owns' a given responsibility. |
| 2 | Data layer vs Model layer: who owns feature stores vs model registries? | Data layer → feature stores (ingestion, storage, feature definitions). Model layer → model registry (versioning, lineage, promotion). Don't mix these up — a top exam trap. |
| 3 | Primary purpose of a feature store | Ensures the SAME feature transformation logic is used in training and serving, preventing training/serving skew. |
| 4 | Primary purpose of a model registry | Tracks model versions, lineage, and stage (e.g., staging → production) for governed deployment. |
| 5 | Batch inference: best use case | Predictions needed on a schedule, not per-request; data changes infrequently (e.g., daily); latency tolerance in minutes/hours. Lower cost, higher throughput. |
| 6 | Real-time inference: best use case | Low-latency, per-request predictions needed immediately (e.g., fraud detection, bidding). Requires always-on serving infrastructure and autoscaling. |
| 7 | Key tradeoff: batch vs real-time inference | Batch = cheaper, higher latency, simpler infra. Real-time = costlier, low latency, requires autoscaling + always-on endpoints. Exam gives a scenario — match latency/cost requirement to approach. |
| 8 | What triggers retraining in a well-designed feedback loop? | Monitored prediction quality degradation or input/output distribution drift crossing a defined threshold — NOT just a fixed calendar schedule or infra errors. |
| 9 | Common exam trap: 5xx serving errors vs model drift | 5xx errors = infrastructure/availability issue. Model drift = data/quality issue. Exam distractors often conflate the two as the same trigger for retraining. |
| 10 | Feedback loop: minimum components required | 1) Log predictions, 2) Capture ground-truth/outcomes, 3) Monitor for drift/quality decay, 4) Automated retraining trigger based on monitored signal. |
| 11 | Scalability consideration: serving layer | Use autoscaling (scale-out/scale-in) tied to real-time load metrics rather than fixed peak-sized provisioning — balances cost vs burst capacity. |
| 12 | Scalability consideration: data layer vs serving layer | Data layer scales for ingestion/storage throughput (e.g., partitioning, distributed storage). Serving layer scales for request concurrency (e.g., autoscaling API replicas). Different scaling levers — exam tests which layer needs which fix. |
