## Chapter 7: The NLP Pipeline: From Text to Transformer-Based Understanding — Practice Questions

**Q1.** A startup has 500 legal documents and needs an interpretable keyword-based search system. The team has no GPU budget and needs to explain why a document matched a query. Which approach BEST meets these requirements?

A) Fine-tune a BERT model for semantic search
B) Use raw bag-of-words counts
C) Train Word2Vec embeddings from scratch on the 500 documents
D) Use TF-IDF vectors with cosine similarity

<details>
<summary>Answer</summary>

**Correct: D**

TF-IDF weights terms by importance (down-weighting common words), is fully interpretable (each dimension = a word), and needs no GPU or training corpus size.

**Why the others are wrong:**
- BERT requires significant compute and is harder to interpret per-term; overkill for a small, interpretable keyword task.
- Raw bag-of-words gives every word equal weight, so common but unimportant words dominate similarity scores — worse than TF-IDF.
- Word2Vec needs a large corpus (millions of tokens) to learn meaningful embeddings; 500 documents is far too small.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A legal analytics tool processes sentences containing the word 'bank' in both financial ('opened a bank account') and geographic ('sat on the river bank') contexts. The system must assign a different vector to 'bank' depending on surrounding words. Which embedding type satisfies this requirement?

A) GloVe embeddings
B) Contextual embeddings (e.g., BERT)
C) Word2Vec Skip-gram embeddings
D) TF-IDF vectors

<details>
<summary>Answer</summary>

**Correct: B**

Contextual embeddings like BERT generate a different vector for the same word depending on its surrounding context, correctly disambiguating polysemous words like 'bank'.

**Why the others are wrong:**
- GloVe produces one static vector per word regardless of context, so both meanings of 'bank' get the identical vector.
- Word2Vec is also static — one fixed embedding per vocabulary word, no context sensitivity.
- TF-IDF is a sparse frequency-based representation with no notion of semantic meaning or context at all.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A compliance team needs to automatically pull out company names, filing dates, and dollar amounts from thousands of uploaded contracts. Which NLP task should be applied?

A) Named Entity Recognition (NER)
B) Sentiment analysis
C) Topic modeling
D) Text summarization

<details>
<summary>Answer</summary>

**Correct: A**

NER is specifically designed to identify and classify spans of text into predefined categories such as ORGANIZATION, DATE, and MONEY — exactly the entities described.

**Why the others are wrong:**
- Sentiment analysis determines emotional tone/polarity, not structured entity extraction.
- Topic modeling (e.g., LDA) discovers latent themes across a document collection, not specific entity spans.
- Summarization condenses text content; it does not extract structured entities like dates or monetary values.

</details>

---

**Q4.** A social media platform needs to classify sentiment on millions of tweets that frequently contain sarcasm, slang, and domain-specific abbreviations, and accuracy is prioritized over latency. Which approach is MOST appropriate?

A) A rule-based lexicon approach (e.g., keyword polarity scoring)
B) Bag-of-words features with a Naive Bayes classifier
C) TF-IDF features with a linear SVM
D) A fine-tuned transformer-based sentiment classifier

<details>
<summary>Answer</summary>

**Correct: D**

Fine-tuned transformer models learn contextual patterns and can pick up on sarcasm and slang far better than static lexicons or sparse bag-of-words models, making them the best fit when accuracy is the priority.

**Why the others are wrong:**
- Rule-based lexicons rely on fixed keyword polarity and fail badly on sarcasm and novel slang not in the lexicon.
- Naive Bayes on bag-of-words ignores word order and context, missing sarcasm cues entirely.
- TF-IDF + SVM is a classical pipeline that also lacks contextual understanding needed for sarcasm detection.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** A preprocessing step needs to quickly reduce 'running', 'runs', and 'ran' toward a common root using simple suffix-stripping rules, accepting that the output may not be a real dictionary word (e.g., 'studies' → 'studi'). Which technique is being described?

A) Lemmatization
B) Tokenization
C) Stop word removal
D) Stemming

<details>
<summary>Answer</summary>

**Correct: D**

Stemming uses fast, rule-based suffix stripping and can produce non-dictionary root forms — the defining tradeoff versus lemmatization.

**Why the others are wrong:**
- Lemmatization uses vocabulary and morphological analysis to return a real dictionary base form, not an approximate stripped root.
- Tokenization splits text into tokens (words/subwords) and does not perform any root reduction.
- Stop word removal eliminates common low-information words (e.g., 'the', 'is') and has nothing to do with root forms.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** Which sequence represents the exam-tested standard order of classical text preprocessing steps before feeding text into a bag-of-words or TF-IDF model?

A) Tokenization → Lowercasing → Stop word removal → Stemming/Lemmatization
B) Stemming → Tokenization → Lowercasing → Stop word removal
C) Stop word removal → Tokenization → Stemming → Lowercasing
D) Lemmatization → Tokenization → Stop word removal → Lowercasing

<details>
<summary>Answer</summary>

**Correct: A**

The standard pipeline splits raw text into tokens first, normalizes case, removes low-information stop words, then reduces remaining tokens to root forms via stemming or lemmatization.

**Why the others are wrong:**
- Stemming cannot be applied before tokenization — there are no individual word units to stem yet.
- Stop word removal requires tokens to already exist, so tokenization must come first, and lowercasing typically precedes stop word matching (which is case-sensitive otherwise).
- Lemmatization requires tokenized, normalized words with part-of-speech context; it can't run before tokenization.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** A standard NER model processes the sentence: 'Microsoft announced the acquisition in Seattle.' Which entity TYPE would correctly be assigned to 'Microsoft'?

A) PERSON
B) ORGANIZATION
C) GPE (Geopolitical Entity)
D) MISC

<details>
<summary>Answer</summary>

**Correct: B**

Company names are classified as ORGANIZATION (ORG), one of the standard NER entity types alongside PERSON, GPE/LOCATION, and DATE.

**Why the others are wrong:**
- PERSON is reserved for individual human names, not company names.
- GPE refers to geopolitical entities like cities or countries (e.g., 'Seattle' in this sentence), not corporations.
- MISC is a catch-all for entities that don't fit standard categories; 'Microsoft' clearly fits the well-defined ORG category.

</details>

---

**Q8.** Which statement correctly differentiates Word2Vec/GloVe embeddings from BERT-style contextual embeddings?

A) Word2Vec/GloVe produce a different vector per occurrence of a word based on context; BERT produces one fixed vector per word
B) Word2Vec/GloVe and BERT both produce identical static vectors, differing only in training speed
C) Word2Vec/GloVe produce one static vector per word regardless of context; BERT produces different vectors depending on surrounding context
D) Word2Vec/GloVe require transformer architectures while BERT uses a shallow neural network

<details>
<summary>Answer</summary>

**Correct: C**

Word2Vec and GloVe are static embedding models — each word maps to exactly one vector learned during training. BERT generates context-dependent vectors, producing different representations for the same word in different sentences.

**Why the others are wrong:**
- This reverses the actual behavior — Word2Vec/GloVe are static, not context-dependent, while BERT is the contextual one.
- They are fundamentally different in representation type (static vs. contextual), not just training speed.
- This reverses the architectures: Word2Vec/GloVe use shallow neural networks (or co-occurrence matrices for GloVe); BERT uses a deep transformer architecture.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

