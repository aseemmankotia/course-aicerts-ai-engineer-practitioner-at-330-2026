## Chapter 5: Transformers, Attention, and What Makes LLMs Powerful — Practice Questions

**Q1.** A company processes 500-page legal contracts and needs a model that understands relationships between clauses on page 2 and page 480 without re-reading the whole document sequentially. Which architectural feature enables this?

A) Self-attention, which lets every token directly weigh relevance to every other token in parallel
B) Recurrent hidden state passed token-by-token like an RNN
C) A larger vocabulary size in the tokenizer
D) Lower temperature setting during inference

<details>
<summary>Answer</summary>

**Correct: A**

Self-attention computes relationships between all token pairs simultaneously, regardless of distance, which is why transformers handle long-range dependencies better than RNNs.

**Why the others are wrong:**
- RNN hidden states degrade over long distances (vanishing gradient) — the opposite of what's needed
- Vocabulary size affects tokenization efficiency, not cross-token relationship modeling
- Temperature controls output randomness, not architectural ability to relate distant tokens

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A legal firm wants an LLM to consistently use proprietary terminology and firm-specific formatting across thousands of future documents, with a budget for a one-time training investment. Which approach BEST meets this requirement?

A) Fine-tuning the pretrained model on a curated dataset of the firm's documents
B) Pretraining a new foundation model from scratch on legal text
C) Using few-shot prompting with 3 examples in every request
D) Increasing the context window size via API configuration

<details>
<summary>Answer</summary>

**Correct: A**

Fine-tuning updates model weights on domain-specific data, baking in terminology and style permanently without needing examples in every prompt — ideal for a one-time investment with long-term consistent reuse.

**Why the others are wrong:**
- Pretraining from scratch requires massive compute/data budgets far beyond a single firm's needs — wasteful and impractical
- Few-shot prompting doesn't persist — it must be repeated every call, increases token cost, and is less consistent
- Context window size is a token limit setting, not a mechanism for teaching the model new behavior

</details>

---

**Q3.** A user submits a 300,000-token document to a model with a 128,000-token context window. What is the MOST likely practical outcome?

A) The model automatically summarizes the document before processing
B) The request is rejected or the content is truncated, causing loss of information beyond the limit
C) The model dynamically increases its context window to fit the input
D) The model processes the full document but with reduced accuracy only on numeric data

<details>
<summary>Answer</summary>

**Correct: B**

Context windows are hard architectural limits; input exceeding the limit is typically rejected by the API or truncated, losing content beyond the boundary.

**Why the others are wrong:**
- Automatic summarization is not a default model behavior — it requires explicit pipeline logic
- Context window size is fixed by the model architecture and cannot dynamically expand at runtime
- The failure mode is content loss/truncation, not selectively reduced accuracy on numbers

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A startup needs to prototype a classification feature using an LLM within one week, with only 20 labeled examples available and no ML engineering team. Which adaptation approach is MOST appropriate?

A) Full fine-tuning on the 20 examples
B) In-context learning (few-shot prompting) using the 20 examples directly in the prompt
C) Pretraining a smaller model from scratch
D) Building a custom tokenizer for the domain vocabulary

<details>
<summary>Answer</summary>

**Correct: B**

In-context learning requires no training infrastructure, no weight updates, and works well with very small example sets — matching the timeline and resource constraints.

**Why the others are wrong:**
- 20 examples is generally insufficient for effective fine-tuning and still requires training infrastructure/time
- Pretraining from scratch demands enormous data and compute, infeasible in a week
- Custom tokenizers address vocabulary coverage, not rapid classification prototyping, and require retraining

</details>

---

**Q5.** Why do modern LLMs use subword tokenization (e.g., Byte-Pair Encoding) instead of whole-word tokenization?

A) It eliminates the need for a context window limit
B) It guarantees the model will never hallucinate
C) It keeps vocabulary size manageable while still representing rare or unseen words by splitting them into known subword units
D) It increases the model's self-attention computational complexity to improve accuracy

<details>
<summary>Answer</summary>

**Correct: C**

Subword tokenization balances vocabulary size against coverage — rare/unknown words are broken into familiar subword pieces, avoiding out-of-vocabulary failures.

**Why the others are wrong:**
- Context window limits are independent of tokenization scheme — they're based on sequence length in tokens
- Tokenization has no relationship to factual accuracy or hallucination
- Increasing computational complexity is a side effect, never a goal, of tokenization design

</details>

---

**Q6.** Which configuration change is MOST effective for reducing factual hallucination in an LLM-powered customer support bot?

A) Increasing the temperature parameter to 1.5
B) Expanding the tokenizer's vocabulary size
C) Switching from fine-tuning to pretraining from scratch
D) Lowering temperature and grounding responses with retrieval-augmented generation (RAG) against a verified knowledge base

<details>
<summary>Answer</summary>

**Correct: D**

Lower temperature reduces random/creative token selection, and RAG grounds outputs in retrieved factual documents rather than relying solely on the model's parametric memory — both directly reduce hallucination.

**Why the others are wrong:**
- Higher temperature increases randomness, which worsens hallucination, not reduces it
- Vocabulary size affects tokenization coverage, not factual grounding
- Pretraining from scratch is a massive undertaking unrelated to fixing hallucination in an existing deployed bot

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** According to compute-optimal scaling laws research (e.g., Chinchilla), what happens when a model's parameter count is scaled up without proportionally increasing training data?

A) The model achieves linearly better performance regardless of data
B) The context window automatically expands to compensate
C) The model becomes undertrained relative to its size, yielding diminishing performance gains per unit of compute
D) Self-attention complexity decreases, speeding up inference

<details>
<summary>Answer</summary>

**Correct: C**

Scaling laws show that compute-optimal training requires balancing parameters and training tokens (roughly proportional scaling); oversized models trained on insufficient data are undertrained and show diminishing returns.

**Why the others are wrong:**
- Performance gains follow a power-law curve with diminishing returns, not linear improvement
- Context window is an architectural choice unrelated to parameter-to-data ratio
- Self-attention complexity depends on sequence length, not parameter count

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** What is the fundamental difference between pretraining and fine-tuning an LLM?

A) Pretraining uses labeled data only, while fine-tuning uses unlabeled data only
B) Pretraining builds general language understanding from a massive, broad corpus; fine-tuning adapts those pretrained weights further using a smaller, task- or domain-specific dataset
C) Pretraining and fine-tuning are identical processes performed at different times
D) Fine-tuning does not update model weights, only pretraining does

<details>
<summary>Answer</summary>

**Correct: B**

Pretraining establishes broad general-purpose capability on large-scale, mostly unlabeled text; fine-tuning specializes the already-trained model using a much smaller, targeted dataset, updating weights further.

**Why the others are wrong:**
- Pretraining typically uses massive unlabeled/self-supervised corpora, not labeled data exclusively — this reverses the reality
- The two processes differ in scale, data, and purpose, not just timing
- Fine-tuning does update model weights — that's what distinguishes it from prompting

</details>

---

