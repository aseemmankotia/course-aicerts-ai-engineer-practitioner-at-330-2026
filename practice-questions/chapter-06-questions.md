## Chapter 6: Applying Generative AI: Prompting, RAG, and Embeddings — Practice Questions

**Q1.** A company's internal policy documents change weekly and the chatbot must always reflect the latest version without retraining a model every time. Which approach BEST meets this requirement?

A) Fine-tune the base model on the policy documents every week
B) Rely on zero-shot prompting with the base model's existing knowledge
C) Fine-tune only the embedding model and skip retrieval
D) Implement RAG: store document chunks in a vector index and re-index whenever documents change

<details>
<summary>Answer</summary>

**Correct: D**

RAG decouples knowledge from the model — updating the vector index re-indexes new content instantly without retraining, which is the correct pattern for frequently changing source data.

**Why the others are wrong:**
- Weekly fine-tuning is expensive, slow, and doesn't guarantee the model reliably recalls new facts — fine-tuning is poor at injecting new factual knowledge
- Zero-shot prompting only uses the model's frozen training data and cannot reflect document updates
- Fine-tuning an embedding model doesn't add retrieval capability or a knowledge store — it changes how text is vectorized, not what content is available

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A legal research assistant must cite the exact source paragraph for every answer and minimize fabricated facts. Latency of 2-3 extra seconds is acceptable. Which design BEST satisfies this?

A) A fine-tuned model that memorizes the case law corpus
B) A zero-shot prompt with no external context
C) A chain-of-thought prompt asking the model to reason from memory
D) A RAG pipeline that retrieves top-k relevant chunks and instructs the model to answer only from retrieved context with citations

<details>
<summary>Answer</summary>

**Correct: D**

RAG grounds generation in retrieved source text, enabling citation of the exact paragraph and reducing hallucination — the core use case RAG is designed for.

**Why the others are wrong:**
- Fine-tuning does not reliably preserve exact source text for citation and increases hallucination risk for precise factual recall
- Zero-shot has no grounding source, so citations would be fabricated
- Chain-of-thought improves reasoning steps but does not provide a verifiable external source for citations

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A developer wants the model to classify customer feedback into exactly three categories using the same output format every time, without any additional training. What technique should be used?

A) Zero-shot prompting
B) Fine-tuning a new model version
C) Few-shot prompting with 2-3 labeled examples showing the desired format
D) Chain-of-thought prompting with step-by-step reasoning

<details>
<summary>Answer</summary>

**Correct: C**

Few-shot prompting shows the model example input/output pairs, which reliably anchors output format and category labels without training.

**Why the others are wrong:**
- Zero-shot gives no format examples, so output format may vary across calls
- Fine-tuning is unnecessary overhead for a simple formatting/classification task solvable with prompt examples
- Chain-of-thought targets multi-step reasoning quality, not output format consistency

</details>

---

**Q4.** Which component is responsible for converting a chunk of text into a numeric vector that captures its semantic meaning for a RAG pipeline?

A) A tokenizer
B) A reranker
C) A diffusion model
D) An embedding model

<details>
<summary>Answer</summary>

**Correct: D**

Embedding models (e.g., text-embedding-3-large) map text into a high-dimensional vector space where semantic similarity corresponds to vector proximity — required for similarity search.

**Why the others are wrong:**
- A tokenizer splits text into tokens; it does not produce semantic vectors
- A reranker reorders already-retrieved results based on relevance, it doesn't generate the original embeddings
- Diffusion models generate images from noise, unrelated to text vector representation

</details>

---

**Q5.** Which service capability allows combining vector similarity search with keyword matching and a semantic ranker in a single query against an indexed document set?

A) Fine-tuning API
B) Zero-shot prompting
C) Diffusion-based image search
D) Hybrid search in a vector database/search service

<details>
<summary>Answer</summary>

**Correct: D**

Hybrid search blends vector (dense) search with traditional keyword (sparse) search and applies semantic re-ranking, improving retrieval quality over vector search alone — the exam tests this combination as the RAG best practice.

**Why the others are wrong:**
- Fine-tuning changes model weights; it has no role in document retrieval
- Zero-shot prompting is a generation technique, not a retrieval mechanism
- Diffusion models are for image generation, not document search

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** By default, most text embedding models use which similarity metric to compare two vectors during a search query?

A) Levenshtein distance
B) Cosine similarity
C) Hamming distance
D) CRC checksum comparison

<details>
<summary>Answer</summary>

**Correct: B**

Cosine similarity measures the angle between two vectors (range -1 to 1) and is the standard default metric for comparing text embeddings in vector search.

**Why the others are wrong:**
- Levenshtein distance measures character-level edit distance between strings, not vector semantics
- Hamming distance compares bit-level differences, used for binary/hash comparisons, not dense text embeddings
- CRC checksums detect data corruption, unrelated to semantic similarity

</details>

---

**Q7.** A prompt engineer appends the phrase 'Let's think through this step by step' to a multi-step math word problem before asking for the final answer. Which prompting technique is this?

A) Chain-of-thought prompting
B) Zero-shot prompting
C) Few-shot prompting
D) Retrieval-augmented prompting

<details>
<summary>Answer</summary>

**Correct: A**

Chain-of-thought prompting explicitly encourages the model to break down reasoning into intermediate steps, improving accuracy on multi-step logical or arithmetic tasks.

**Why the others are wrong:**
- Zero-shot provides no reasoning scaffold or examples, just the task instruction
- Few-shot relies on labeled input/output examples, not a reasoning instruction phrase
- Retrieval-augmented prompting involves injecting external retrieved context, not a reasoning cue

</details>

---

**Q8.** At a conceptual level, how does a diffusion model generate an image from a text prompt?

A) It retrieves the closest matching image from a database and returns it directly
B) It fine-tunes a language model on pixel data for each request
C) It applies a single-pass transformation converting text tokens directly into pixel values
D) It starts from random noise and iteratively denoises it over multiple steps, guided by the text embedding, until a coherent image emerges

<details>
<summary>Answer</summary>

**Correct: D**

Diffusion models learn to reverse a gradual noising process; generation runs this reverse (denoising) process step-by-step conditioned on the text embedding to produce an image.

**Why the others are wrong:**
- This describes retrieval-based image search, not generative diffusion
- Diffusion models don't fine-tune per request; they run inference through a pretrained denoising network
- Image generation is iterative over many denoising steps, not a single-pass direct mapping

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

