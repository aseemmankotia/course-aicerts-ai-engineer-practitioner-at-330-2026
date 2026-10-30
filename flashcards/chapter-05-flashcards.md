## Chapter 5: Transformers, Attention, and What Makes LLMs Powerful — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Self-attention computational complexity relative to sequence length n? | O(n²) — cost grows quadratically with sequence length. Exam tip: this is the root technical reason context windows have hard limits. |
| 2 | RNN vs Transformer: how do they process a sequence? | RNN: sequentially, one token at a time (hard to parallelize, long-range info decays). Transformer: all tokens in parallel via self-attention (captures long-range dependencies directly). Exam tip: parallelism is why transformers train faster on GPUs. |
| 3 | Do pretraining, fine-tuning, and prompting each update model weights? | Pretraining: yes. Fine-tuning: yes (on a smaller dataset). Prompting/in-context learning: no — only the input is conditioned, weights stay frozen. Exam tip: prompting is cheapest and fastest but least persistent. |
| 4 | Claude 3 family context window size? | 200,000 tokens (~150,000 words). Exam tip: large context windows reduce need for chunking but increase latency and cost per call. |
| 5 | GPT-4 Turbo context window size? | 128,000 tokens. Exam tip: compare context windows across models when the scenario involves long documents. |
| 6 | Primary cause of LLM hallucination? | The model predicts statistically likely next tokens, not verified facts — it has no built-in fact-checking mechanism. Exam tip: mitigate with RAG (retrieval-augmented generation) or lower temperature. |
| 7 | Purpose of subword tokenization (e.g., Byte-Pair Encoding)? | Splits rare/unknown words into common subword units, keeping vocabulary size manageable (typically 30K–100K tokens) while still covering any input text. Exam tip: avoids the out-of-vocabulary problem. |
| 8 | Chinchilla scaling law key insight? | Compute-optimal training balances parameter count and training tokens (~20 training tokens per parameter). Exam tip: many early large models were undertrained relative to their size. |
| 9 | What happens when input exceeds a model's context window? | Request is rejected or oldest/excess tokens are truncated, causing loss of information. Exam tip: use chunking + retrieval (RAG) for documents exceeding the window, not just hoping it fits. |
| 10 | Self-attention mechanism purpose, one sentence? | Lets every token weigh its relevance to every other token in the sequence simultaneously, capturing long-range dependencies without sequential processing. Exam tip: this replaces the RNN sequential bottleneck. |
| 11 | In-context learning (few-shot prompting) — does it require a training dataset or gradient updates? | No — examples are placed directly in the prompt at inference time; no weights change. Exam tip: fastest adaptation method but constrained by context window size. |
| 12 | What does 'diminishing returns' mean in LLM scaling laws? | Beyond a certain scale, adding more parameters/data yields progressively smaller loss/accuracy improvements per unit of added compute (power-law decay, not linear). Exam tip: data quality and architecture matter more than brute-force size increases past this point. |
