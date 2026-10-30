# Chapter 5 Cheat Sheet: Transformers, Attention & LLM Power

## Self-Attention vs RNN
| Feature | RNN | Transformer (Self-Attention) |
|---|---|---|
| Processing order | Sequential, one token at a time | Parallel, all tokens at once |
| Long-range dependencies | Degrade over distance | Direct token-to-token weighting |
| Training speed on GPU | Slow (can't parallelize) | Fast (parallelizable) |
| Complexity | O(n) per step, n steps total | O(n²) per layer |

**Exam note:** Self-attention's core purpose = let every token directly relate to every other token, regardless of distance, in parallel.

## Pretraining vs Fine-Tuning vs Prompting
| Method | Weights updated? | Data needed | Use case | Cost/Time |
|---|---|---|---|---|
| Pretraining | Yes (from scratch) | Massive unlabeled corpus | Build foundation model | Very high |
| Fine-tuning | Yes (on top of pretrained) | Smaller labeled/domain dataset | Specialize to domain/style | Moderate |
| Prompting / In-context learning | No | Examples in the prompt only | Quick prototyping, low data | Low, instant |

**Exam trap:** Students often assume prompting changes model behavior permanently — it does not; it's per-request conditioning only.

## Context Windows (reference values)
| Model | Context Window |
|---|---|
| GPT-4 Turbo | 128,000 tokens |
| Claude 3 family | 200,000 tokens |

**Practical impact of exceeding window:** request rejected or oldest content truncated → information loss. Fix: chunking + retrieval-augmented generation (RAG), not relying on raw window size.

## Tokenization
- Subword tokenization (e.g., Byte-Pair Encoding) splits rare words into known subword units.
- Typical vocabulary size: ~30K–100K tokens.
- Avoids out-of-vocabulary failures while keeping vocabulary manageable.

## Hallucination — Causes & Mitigations
| Cause | Mitigation |
|---|---|
| Model predicts plausible, not verified, tokens | Retrieval-Augmented Generation (RAG) |
| High randomness in sampling | Lower temperature |
| No grounding in fact source | Cite sources / structured grounding |

## Scaling Laws
- Chinchilla finding: compute-optimal training ≈ 20 training tokens per parameter.
- Oversized models with insufficient data = undertrained, diminishing returns.
- Loss follows a power-law decay with scale — not linear improvement.

**Exam note:** "More parameters" alone is a commonly wrong answer when the scenario is about compute-optimal or cost-efficient scaling — data quantity/quality matters equally.
