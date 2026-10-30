# Answer Key — Practice Test 2

**Q1. Correct: A**

Semi-supervised learning is explicitly designed for this ratio: a small amount of labeled data anchors the model while a large unlabeled pool provides structure, which is far more data-efficient than discarding 97% of the dataset.

---

**Q2. Correct: A**

An agent taking sequential actions in an environment and receiving a delayed scalar reward is the defining structure of reinforcement learning, and the classic difficulty of linking a delayed outcome back to the specific action responsible is the credit assignment problem.

---

**Q3. Correct: B**

Repeatedly evaluating and selecting configurations against the same held-out split turns it into a de facto validation set that the model indirectly 'leaks' into; reporting its score as final performance overstates real-world generalization. The correct workflow uses a separate untouched test set, evaluated only once, for the final reported metric.

---

**Q4. Correct: C**

A feedback loop that captures real-world outcomes and compares them to predictions is the only mechanism that detects concept/data drift causing silent accuracy degradation, since infrastructure metrics (latency, errors) won't reveal it.

---

**Q5. Correct: C**

The data layer owns ingestion pipelines, cleaning, feature engineering, and validation/schema enforcement so downstream model components receive consistent, well-formed inputs.

---

**Q6. Correct: B**

A serverless autoscaling endpoint matches unpredictable traffic patterns, automatically scales up during business hours, and scales to zero overnight to minimize cost — the exact requirement stated.

---

**Q7. Correct: B**

AT-330 architecture separates the model layer (training, experimentation, versioning, artifact storage) from the serving layer (deploying that artifact behind an inference endpoint for consumption).

---

**Q8. Correct: C**

Separating concerns into a versioned data pipeline, distinct real-time and batch model components, and a logging feedback loop satisfies real-time alerting, scheduled retraining, and audit traceability simultaneously — the three explicit requirements.

---

**Q9. Correct: D**

Sigmoid saturates for large positive/negative inputs, producing derivatives near zero that shrink multiplicatively through many layers during backpropagation (vanishing gradients). ReLU has a constant gradient of 1 for positive inputs, allowing gradient signal to reach early layers.

---

**Q10. Correct: A**

A large, widening gap between training and validation accuracy is a textbook sign of overfitting. Dropout randomly deactivates neurons during training, preventing co-adaptation and forcing the network to learn more generalizable features without reducing architecture size.

---

**Q11. Correct: C**

Sigmoid squashes the single output neuron into a (0,1) range interpretable as a probability, and binary cross-entropy is the loss function derived for that probabilistic interpretation, giving well-behaved gradients.

---

**Q12. Correct: C**

Wild loss oscillation followed by NaN values is a classic sign of exploding gradients caused by too large a learning rate. Lowering the learning rate and/or clipping gradient norms bounds the size of weight updates and stabilizes training.

---

**Q13. Correct: A**

A single-layer perceptron computes a weighted sum passed through a step/threshold function, which can only separate classes with a single hyperplane. XOR's four points cannot be separated by any single straight line, so no weight configuration solves it; a hidden layer is required to create a nonlinear decision boundary.

---

**Q14. Correct: C**

Gradients growing unboundedly across timesteps is the exploding gradient problem, common in RNNs due to repeated multiplication through backpropagation through time. Gradient clipping rescales the gradient vector when its norm exceeds a threshold, directly bounding update magnitude and stabilizing training.

---

**Q15. Correct: D**

The described pattern — falling training loss with rising validation loss after a point — is the textbook signature of overfitting. Dropout and L2 regularization reduce the network's reliance on specific weights/co-adapted neurons, and early stopping halts training at the point of best generalization (around epoch 12 here), directly targeting the root cause.

---

**Q16. Correct: C**

LSTMs use gated cell states specifically designed to preserve gradient flow across long sequences, allowing information from 150+ tokens earlier to be retained and selectively forgotten or passed forward, directly solving the vanishing gradient problem that cripples vanilla RNNs on long-range dependencies.

---

**Q17. Correct: B**

Single-stage detectors process the full image in one forward pass through a single network, directly predicting boxes and classes simultaneously, which gives the low end-to-end latency (well under 50ms on optimized embedded hardware) required for real-time autonomous driving perception.

---

**Q18. Correct: A**

Using the standard convolution output formula (W - F + 2P) / S + 1 = (32 - 5 + 0) / 1 + 1 = 28, the output feature map is 28x28 spatially (with 16 channels from the 16 filters), which is the exact calculation the exam tests for conv layer sizing.

---

**Q19. Correct: B**

Transformer self-attention requires every token to attend to every other token, producing O(n^2) compute and memory cost as sequence length grows, which explains disproportionate latency and cost increases well before the hard context limit is hit.

---

**Q20. Correct: D**

Parameter-efficient fine-tuning methods like LoRA adapt a small set of additional weights atop a frozen pretrained model, specializing style/domain behavior cheaply while preserving the base model's broad language competence — exactly matching the budget and preservation constraints.

---

**Q21. Correct: A**

GPT-family models use Byte-Pair Encoding, which starts from individual bytes/characters and iteratively merges the most frequent adjacent pairs to build a fixed-size subword vocabulary, allowing efficient representation of both common words and rare/unseen terms.

---

**Q22. Correct: A**

LLMs are next-token prediction systems trained to produce plausible, fluent continuations based on learned statistical patterns; they have no built-in fact-verification mechanism, which is why they can generate confident, fluent, but factually false content such as fabricated citations.

---

**Q23. Correct: D**

Retrieval is already working correctly (relevant passages are consistently returned), so the failure is in generation: the model is not adhering to the retrieved context and is hallucinating confident-sounding citations. The fix is grounding the prompt explicitly and adding a post-generation verification step that checks citations against the actual retrieved metadata, not changing the retrieval pipeline.

---

**Q24. Correct: D**

Cosine similarity divides by the product of the vector magnitudes as part of its calculation, making it invariant to vector length. This is the correct choice when embeddings are not pre-normalized, since it isolates the angular (semantic direction) similarity regardless of magnitude differences between vectors.

---

**Q25. Correct: A**

Classifier-free guidance scale directly controls the trade-off between prompt fidelity and image naturalness/diversity. Increasing CFG scale pushes the diffusion process to weight the text conditioning more heavily, producing images that follow the prompt more literally at the cost of diversity and sometimes introducing artifacts.

---

**Q26. Correct: A**

RAG decouples the knowledge source from the model itself: updating the retrievable data store immediately makes new information available at query time, with no retraining required, ensuring responses stay current and cost-effective.

---

**Q27. Correct: D**

Lemmatization uses a dictionary and part-of-speech context to return the correct base/dictionary form (lemma), correctly handling irregular forms like 'better' -> 'good', which rule-based suffix stripping cannot do.

---

**Q28. Correct: D**

Transformer-based contextual embeddings generate a distinct vector for each occurrence of a word based on its surrounding context via self-attention, correctly disambiguating polysemous terms like 'bank'.

---

**Q29. Correct: B**

'I' (Inside) indicates the token is a continuation of the entity span opened by the preceding 'B' (Beginning) tag of the same type, meaning all three tokens together form one ORG entity.

---

**Q30. Correct: D**

ABSA explicitly extracts aspect terms ('battery life', 'camera') and assigns sentiment polarity to each independently, preserving mixed-sentiment nuance that document-level scoring averages away.

---

**Q31. Correct: D**

BPE builds a subword vocabulary by iteratively merging the most frequent adjacent symbol pairs, allowing rare or unseen words to be decomposed into known subword units instead of being dropped or mapped to a generic UNK token.

---

**Q32. Correct: A**

Standard self-attention computes pairwise attention scores between every pair of tokens in the sequence, resulting in an n x n attention matrix and O(n^2) time and memory complexity, a well-known limitation tested on the exam.

---

**Q33. Correct: C**

Transformer-based contextual embeddings (e.g., BERT) generate a different vector representation for the same word depending on its surrounding context, directly solving the word-sense disambiguation problem that static embeddings like Word2Vec or GloVe cannot handle since those produce exactly one vector per vocabulary word regardless of usage.

---

**Q34. Correct: C**

LoRA (via PEFT) freezes the pretrained weights and trains small low-rank adapter matrices, drastically cutting the number of trainable parameters and GPU memory needed for optimizer states, making it feasible to fine-tune large models on consumer GPUs.

---

**Q35. Correct: A**

Each pretrained checkpoint has its own tokenizer and vocabulary mapping. Using a tokenizer from a different checkpoint produces token IDs that map to entirely different subwords in the model's embedding table, silently corrupting inputs rather than raising an obvious error.

---

**Q36. Correct: D**

DataCollatorWithPadding pads each batch dynamically to the length of the longest sequence within that batch at collation time, which is more memory- and compute-efficient than padding everything to a fixed global max length.

---

**Q37. Correct: C**

ignore_mismatched_sizes=True tells from_pretrained to skip loading the incompatible classification head weights (since 3 vs 5 labels differ in shape) while still loading all matching encoder layers, then randomly initializes the new head for fine-tuning.

---

**Q38. Correct: D**

The zero-shot-classification pipeline uses an NLI-based model to score arbitrary candidate labels against input text without requiring any task-specific fine-tuning or labeled training data, exactly matching the scenario's constraint of unseen categories.

---

**Q39. Correct: B**

push_to_hub() serializes the model weights/config and tokenizer files and uploads them to the specified Hub repository, enabling anyone with access to load the artifact later via AutoModel.from_pretrained or AutoTokenizer.from_pretrained.

---

**Q40. Correct: B**

GPT-2's tokenizer has no dedicated pad token by design. The standard, documented fix is to reuse the EOS token as the pad token (tokenizer.pad_token = tokenizer.eos_token) and ensure attention_mask correctly marks padded positions as non-attended, so the model ignores padding without altering vocabulary size or embedding dimensions.

---

**Q41. Correct: B**

Gradio natively supports streaming outputs when the backend function is a generator that yields incremental values; the output component updates on each yield, giving true token-by-token streaming UX.

---

**Q42. Correct: B**

Disabling the trigger control and showing a loading indicator during inference communicates system state to the user, prevents duplicate submissions, and is a core UX pattern for AI apps with non-trivial latency.

---

**Q43. Correct: B**

Streamlit provides first-class support for multipage apps, a dedicated sidebar API, and rich layout containers (columns, tabs, expanders), making it better suited than Gradio for data-dashboard-style apps with heavy custom layout needs.

---

**Q44. Correct: B**

Gradio's built-in queue() system with a configured concurrency_limit throttles simultaneous backend calls so requests are processed sequentially (or up to a safe limit) instead of overwhelming a single-instance model, preventing crashes.

---

**Q45. Correct: A**

Separating user-controlled input from the trusted system prompt, and validating/sanitizing that input before prompt construction, is the key architectural defense against prompt injection reaching or overriding system-level instructions.

---

**Q46. Correct: C**

Rising false negatives with no infrastructure or schema change is a classic symptom of data or concept drift — the statistical relationship between inputs and outputs has shifted in production. Monitoring feature and prediction distributions against the training baseline is the standard MLOps practice for catching this before it affects business outcomes.

---

**Q47. Correct: C**

Running gunicorn with multiple uvicorn worker processes is the standard production pattern for ASGI apps like FastAPI — it provides process-level concurrency, worker recycling, and resilience that a single dev server lacks, and explicitly binds to a reachable host/port for container networking.

---

**Q48. Correct: D**

Canary deployment incrementally shifts a small, growing percentage of live traffic to the new version while monitoring real business metrics, allowing fast rollback if problems appear — exactly matching the 5%-then-gradual-increase pattern described.

---

