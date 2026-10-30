# Chapter 7 Cheat Sheet: NLP Pipeline

## Classical Preprocessing Order (EXAM-TESTED)
1. **Tokenization** — split text into words/subwords
2. **Lowercasing** — normalize case
3. **Stop word removal** — drop low-info words (the, is, and)
4. **Stemming/Lemmatization** — reduce to root form

## Stemming vs Lemmatization
| Feature | Stemming | Lemmatization |
|---|---|---|
| Method | Rule-based suffix stripping | Dictionary/morphology lookup |
| Speed | Fast | Slower |
| Output | May be non-word ('studi') | Real word ('study') |
| Needs POS? | No | Often yes |

## Bag-of-Words vs TF-IDF vs Dense Embeddings
| Method | Representation | Captures Meaning? | Best For |
|---|---|---|---|
| Bag-of-Words | Sparse word counts | No | Simple baselines |
| TF-IDF | Sparse, weighted by importance | No | Small data, interpretable search |
| Word2Vec/GloVe | Dense, static vector/word | Partial (no context) | Similarity on large corpora |
| BERT (contextual) | Dense, context-dependent | Yes (handles polysemy) | Semantic tasks, disambiguation |

## Static vs Contextual Embeddings
- **Word2Vec / GloVe**: one fixed vector per word, trained via co-occurrence (GloVe) or skip-gram/CBOW (Word2Vec). Typical dims: 100–300.
- **BERT**: transformer-based, generates a *different* vector per word depending on sentence context. BERT-base = 768 dims, BERT-large = 1024 dims.
- Exam trap: questions describing "same word, different meaning, different vector" → always point to **contextual embeddings**, never Word2Vec/GloVe.

## Named Entity Recognition (NER)
Task: locate and classify spans of text into categories.
Common types: **PERSON, ORGANIZATION (ORG), GPE/LOCATION, DATE, TIME, MONEY, PERCENT, MISC**
Exam trap: company name → ORG (not MISC or PERSON); city/country → GPE.

## Sentiment Analysis Approaches
| Approach | How it works | Strength | Weakness |
|---|---|---|---|
| Rule-based (lexicon) | Keyword polarity scoring | Fast, no training | Fails on sarcasm/slang |
| Model-based | Trained/fine-tuned classifier | Handles context, sarcasm | Needs more compute/data |

## Classical vs Transformer NLP Pipelines
| Aspect | Classical (TF-IDF/BoW) | Transformer-based |
|---|---|---|
| Preprocessing | Heavy (stemming, stop words) | Minimal (subword tokenization only) |
| Context awareness | None | Full contextual understanding |
| Compute cost | Low | High |
| Data needs | Works with small data | Benefits from large pretraining + fine-tuning data |
| Interpretability | High | Lower |

## Quick Decision Rule
- Small data + interpretability + low compute → **TF-IDF**
- Need semantic similarity, polysemy handling, best accuracy → **Contextual embeddings (BERT)**
- Need structured entity extraction → **NER**
- Need sarcasm-aware sentiment → **Model-based (fine-tuned transformer)**, not rule-based lexicon
