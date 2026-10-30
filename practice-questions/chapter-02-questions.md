## Chapter 2: The Architecture of Modern AI Systems — Practice Questions

**Q1.** A streaming ad-bidding platform must score each incoming request and return a bid decision within 50ms, with traffic spikes up to 10x during peak hours. Which serving approach BEST meets these requirements?

A) Nightly batch scoring job that writes predictions to a lookup table
B) A scheduled hourly micro-batch job that processes requests in 15-minute windows
C) A manual on-demand script triggered by an operations engineer
D) Low-latency real-time inference API behind an autoscaling load balancer

<details>
<summary>Answer</summary>

**Correct: D**

Sub-second latency with variable, bursty traffic requires a real-time serving endpoint that can autoscale horizontally behind a load balancer.

**Why the others are wrong:**
- Batch scoring pre-computes predictions before the request arrives, which fails for live, per-request bidding decisions that depend on current context.
- Micro-batching still introduces windowed delay (minutes), violating the 50ms requirement.
- A manually triggered script cannot meet latency or scale requirements and has no automated availability guarantee.

</details>

---

**Q2.** A team notices that a deployed model's prediction accuracy has been silently degrading over three months because the input data distribution shifted, but no alert fired. What is the ROOT architectural gap?

A) The model was trained with too few epochs
B) The serving layer is using batch inference instead of real-time inference
C) There is no feedback loop capturing live predictions and ground-truth outcomes to detect drift and trigger retraining
D) The feature store schema was not versioned

<details>
<summary>Answer</summary>

**Correct: C**

Without logging predictions and outcomes and comparing them against baseline distributions, drift goes undetected — this is exactly what a feedback loop with monitoring and retraining triggers is designed to catch.

**Why the others are wrong:**
- Training epochs affect initial model fit, not post-deployment drift detection.
- Batch vs real-time serving is an inference latency/throughput decision, unrelated to detecting accuracy decay.
- Feature schema versioning helps prevent training/serving skew but does not by itself detect live data drift without monitoring.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A retail company generates personalized product recommendations. Catalog and user behavior data only materially change once per day, and recommendations are shown on a web page with no strict latency requirement below one second. Which inference strategy is MOST cost-effective?

A) Batch inference run nightly, with results cached and served from a lookup store
B) Real-time inference API called on every page load
C) Streaming inference triggered on every user click event
D) Synchronous inference embedded directly in the database layer

<details>
<summary>Answer</summary>

**Correct: A**

Since underlying data changes only daily and latency tolerance is loose, nightly batch inference with cached results avoids the operational cost and complexity of a real-time serving tier while still meeting requirements.

**Why the others are wrong:**
- Real-time inference on every page load adds unnecessary compute cost and latency overhead when data doesn't change intraday.
- Streaming on every click event is excessive given daily-granularity data changes and adds unneeded infrastructure complexity.
- Embedding inference directly in the database layer tightly couples compute to storage and is not a recognized serving pattern for scalable ML systems.

</details>

---

**Q4.** Which architectural component is responsible for ensuring that the exact same feature transformation logic is used during both model training and online serving, preventing training/serving skew?

A) Model registry
B) Inference API gateway
C) Data ingestion pipeline
D) Feature store

<details>
<summary>Answer</summary>

**Correct: D**

A feature store centralizes feature definitions and computation so the same logic produces consistent values for both offline training and online serving, eliminating skew.

**Why the others are wrong:**
- The model registry tracks versioned model artifacts and stage transitions, not feature computation logic.
- The inference API gateway routes and serves prediction requests but does not own feature transformation consistency.
- The ingestion pipeline moves raw data into storage; it does not guarantee consistent feature logic across environments.

</details>

---

**Q5.** Which component tracks model versions, their lineage, and promotion status (e.g., staging to production)?

A) Data lake
B) Feature store
C) Model registry
D) Serving API

<details>
<summary>Answer</summary>

**Correct: C**

The model registry is the catalog that stores versioned model artifacts, metadata, lineage, and stage (e.g., staging/production) for governed promotion.

**Why the others are wrong:**
- A data lake stores raw and processed data, not model version metadata.
- A feature store manages feature definitions and values, not model lifecycle state.
- The serving API exposes a deployed model for inference but does not track versioning or lineage history.

</details>

---

**Q6.** In a well-designed feedback loop, what should primarily trigger an automated model retraining job, rather than a fixed calendar schedule alone?

A) A manual request from the product manager
B) The serving API returning any 5xx error
C) A new engineer joining the ML team
D) Monitored degradation in prediction quality or detected input/output distribution drift against a defined threshold

<details>
<summary>Answer</summary>

**Correct: D**

Feedback loops should log predictions and outcomes, continuously monitor for drift or performance decay against a defined threshold, and trigger retraining based on that signal rather than relying purely on a fixed schedule.

**Why the others are wrong:**
- Manual requests are not automated and don't scale as a systematic retraining trigger.
- 5xx errors indicate infrastructure/availability failures, not model quality degradation — conflating these is a common exam trap.
- Team staffing changes have no technical bearing on when a model needs retraining.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** A company needs to scale their serving layer to handle an unpredictable 20x traffic surge during flash sales without over-provisioning cost during normal periods. Which configuration BEST addresses this?

A) Provision a fixed number of servers sized for peak traffic at all times
B) Deploy inference behind an autoscaling group with scale-out/scale-in policies based on request load
C) Switch entirely to batch inference during the sale
D) Manually add servers when engineers notice latency increasing

<details>
<summary>Answer</summary>

**Correct: B**

Autoscaling policies tied to real-time load metrics let the serving layer scale out during surges and scale back in afterward, balancing cost and performance.

**Why the others are wrong:**
- Fixed peak-sized provisioning guarantees capacity but wastes cost during the 95%+ of time traffic is normal.
- Batch inference cannot serve live, request-driven traffic during a flash sale with real-time user interaction.
- Manual scaling introduces latency in response time and human error risk during a fast-moving traffic spike.

</details>

---

**Q8.** Which statement correctly distinguishes the responsibilities of the model layer from the serving layer in a modern AI architecture?

A) The model layer handles raw data ingestion, while the serving layer handles feature engineering
B) The model layer is responsible for training, versioning, and registering models, while the serving layer is responsible for exposing trained models via inference APIs to deliver predictions
C) The model layer and serving layer are the same component with different names
D) The model layer logs predictions for monitoring, while the serving layer trains new models

<details>
<summary>Answer</summary>

**Correct: B**

The model layer owns training, versioning, and registry management; the serving layer owns deploying those trained artifacts behind inference APIs (batch or real-time) to generate predictions for consumers.

**Why the others are wrong:**
- Raw data ingestion and feature engineering belong to the data layer, not the model or serving layers.
- They are distinct layers with different responsibilities and are commonly deployed as separate scalable components.
- This reverses responsibilities — logging/monitoring for feedback typically spans the serving layer outward to the feedback loop, and training belongs to the model layer, not serving.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

