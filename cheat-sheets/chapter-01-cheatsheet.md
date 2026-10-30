## Chapter 1 Cheat Sheet — AI Engineering Foundations & Exam Blueprint

### AT-330 Exam Structure
| Attribute | Value |
|---|---|
| Total questions | 50 |
| Time limit | 90 minutes |
| Avg time/question | ~1.8 min |
| Passing score | 35/50 (70%) |
| Domain weight (this chapter) | 5% |

### Learning Paradigms
| Type | Data | Goal | Example |
|---|---|---|---|
| Supervised | Labeled | Predict known output | Spam classification |
| Unsupervised | Unlabeled | Discover structure | Customer segmentation (clustering) |
| Reinforcement | Reward signal from environment | Maximize cumulative reward | Game-playing agent |

**Exam trap:** A question describing rewards/penalties is RL, not supervised learning — do not confuse 'trial and error improvement' with 'labeled training.'

### Standard ML Workflow (order matters)
1. Data collection
2. Preprocessing
3. Training
4. Evaluation
5. Deployment
6. Monitoring

**Exam trap:** Evaluation happens BEFORE deployment (validating a candidate model); Monitoring happens AFTER deployment (tracking live performance/drift). These are commonly swapped on exams.

### Role Boundaries
| Role | Primary Focus |
|---|---|
| Data Scientist | Exploratory analysis, feature engineering, model experimentation |
| AI/ML Engineer | Production pipelines, APIs, scaling, serving infrastructure |
| Research Scientist | Novel algorithm/model development |

**Exam trap:** 'Who builds the deployment pipeline' = AI/ML engineer, not data scientist.

### Vendor-Neutral vs Vendor-Specific
- **Vendor-neutral (AT-330):** transferable concepts — workflow, learning types, lifecycle, role boundaries.
- **Vendor-specific certs:** tied to one provider's SDK, CLI, and service names.

**Exam trap:** Don't expect platform-specific API names on AT-330 — focus on concepts that apply regardless of cloud provider.

### Prerequisite Skills Check
- **Python:** lists, dicts, functions, basic loops (e.g., `sum(data)/len(data)` for mean).
- **Statistics:** mean, median, standard deviation, basic probability — no calculus required.

If either prerequisite feels shaky, review before Chapter 2 — later chapters assume this foundation without re-teaching it.
