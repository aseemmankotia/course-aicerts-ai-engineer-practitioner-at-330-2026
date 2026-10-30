## Chapter 8: Transfer Learning in Practice with the Hugging Face Ecosystem — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Default learning_rate in TrainingArguments (if unspecified)? | 5e-05. Exam tip: Trainer uses AdamW with this default — much lower than typical from-scratch training rates since weights are already pretrained. |
| 2 | Default num_train_epochs in TrainingArguments? | 3. Exam tip: fine-tuning pretrained models needs far fewer epochs than training from scratch — 2-4 epochs is typically sufficient. |
| 3 | AutoModel class for encoder-decoder models like T5 or BART? | AutoModelForSeq2SeqLM. Exam tip: use for summarization, translation, and text-to-text generation tasks. |
| 4 | AutoModel class for decoder-only models like GPT-2? | AutoModelForCausalLM. Exam tip: causal = autoregressive, predicts the next token only, no bidirectional context. |
| 5 | AutoModel class for encoder-only masked-word prediction like BERT? | AutoModelForMaskedLM. Exam tip: use AutoModelForSequenceClassification instead for classification tasks on the same checkpoint. |
| 6 | pipeline('sentiment-analysis') default model? | distilbert-base-uncased-finetuned-sst-2-english. Exam tip: pipeline() always picks a sensible default checkpoint if model= isn't specified. |
| 7 | Code to freeze all transformer layers except the classification head? | for name, param in model.named_parameters(): if 'classifier' not in name: param.requires_grad = False. Exam tip: requires_grad=False stops gradient updates for that tensor. |
| 8 | When should you prefer full fine-tuning over freezing layers? | Large labeled dataset (100k+ examples) plus ample compute. Exam tip: full fine-tuning adapts all layers for best accuracy but risks overfitting on small datasets. |
| 9 | When should you prefer freezing the encoder and training only a head? | Small dataset (hundreds to low thousands of examples) and/or limited compute. Exam tip: drastically reduces trainable params and prevents catastrophic forgetting of pretrained features. |
| 10 | pipeline() API vs manual AutoTokenizer+AutoModel — when is manual required? | When you need custom tokenization params (max_length, truncation), raw logits, or batching control. Exam tip: pipeline() applies its own default pre/post-processing you can't easily override. |
| 11 | datasets library: how to apply tokenization efficiently to a whole dataset? | dataset.map(tokenize_fn, batched=True). Exam tip: batched=True processes multiple examples per call, much faster than row-by-row. |
| 12 | Why must AutoTokenizer and AutoModel checkpoints match exactly? | Tokenizer defines the vocabulary/token-ID mapping the model was trained with. Exam tip: mismatched tokenizer/model (e.g., gpt2 tokenizer with a bert model) silently produces garbage input IDs — no error is raised. |
