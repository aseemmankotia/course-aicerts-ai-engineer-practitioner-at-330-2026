# Chapter 6 Cheat Sheet — Prompting, RAG, Embeddings

## Prompting Techniques
| Technique | Definition | Use When |
|---|---|---|
| Zero-shot | Instruction only, no examples | Simple, well-known tasks |
| Few-shot | Instruction + 2-3 labeled examples | Need consistent output format/labels |
| Chain-of-thought (CoT) | Model reasons step-by-step before final answer | Multi-step math/logic problems |

**Exam note:** Match technique to the failure mode — inconsistent format → few-shot; wrong multi-step logic → CoT.

## RAG Pipeline (5 Stages)
1. Chunk documents
2. Embed chunks → vectors
3. Store vectors in vector index
4. Embed query → retrieve top-k similar chunks
5. Augment prompt with retrieved chunks → generate grounded answer

**Exam note:** Retrieval ALWAYS happens before generation. Re-indexing updates knowledge without retraining the model.

## RAG vs Fine-tuning
| Need | Choose |
|---|---|
| Frequently changing knowledge | RAG |
| Source citations / grounding | RAG |
| Reduce factual hallucination | RAG |
| Change tone/style/format | Fine-tuning |
| Teach a narrow skill/behavior | Fine-tuning |

**Common trap:** Fine-tuning does NOT reliably inject new facts — it changes behavior, not a knowledge base.

## Embeddings & Vector Search
- Embedding = vector representation of text meaning; similar meaning → vectors close together.
- Default similarity metric: **cosine similarity** (range -1 to 1).
- ANN search commonly uses **HNSW** graph indexing for speed at scale.
- **Hybrid search** = vector search + keyword search + semantic re-ranker → best retrieval quality for RAG.

**Exam trap:** Picking "vector search only" when the scenario implies exact keyword matches are also required (e.g., product SKUs) — hybrid search is the better answer.

## Chunking Guidance
- Chunks too large → diluted relevance, wasted context window.
- Chunks too small → lost surrounding context.
- Use moderate chunk size with slight overlap between chunks.

## Diffusion Models (Conceptual)
- Generation = iterative **denoising** of random noise, conditioned on a text embedding.
- NOT a single-pass text-to-pixel transformation; NOT retrieval-based.

## GenAI Product Design Tradeoffs
| Factor | Smaller Model | Larger Model |
|---|---|---|
| Latency | Lower | Higher |
| Cost | Lower | Higher |
| Reasoning quality | Weaker | Stronger |

**Key risks to always evaluate:** latency, cost, hallucination risk.
**Exam trap:** RAG reduces hallucination risk but does NOT by itself reduce latency or cost — retrieval adds an extra step.
