## Chapter 8 Cheat Sheet: Transfer Learning with Hugging Face

### Auto Class Pairing (checkpoint → head)
| Architecture Type | Example Checkpoint | Correct AutoModel Class |
|---|---|---|
| Encoder-only (bidirectional) | bert-base-uncased | AutoModelForSequenceClassification / AutoModelForMaskedLM / AutoModelForTokenClassification |
| Decoder-only (autoregressive) | gpt2 | AutoModelForCausalLM |
| Encoder-decoder (seq2seq) | t5-small, bart-large | AutoModelForSeq2SeqLM |
| Span extraction | bert-base-uncased | AutoModelForQuestionAnswering |

**Rule:** tokenizer checkpoint name MUST match model checkpoint name — mismatched vocab silently corrupts inputs with no error.

### Freeze vs Full Fine-Tune Decision Table
| Condition | Strategy |
|---|---|
| Small dataset (hundreds–low thousands), limited compute | Freeze encoder, train only head |
| Large dataset (100k+), ample compute (multi-GPU) | Full fine-tune all layers, small LR |
| Domain very different from pretraining corpus | Full fine-tune (if enough data) |
| Need fast iteration / low cost | Freeze encoder (fewer trainable params) |

**Freeze code:**
```python
for name, param in model.named_parameters():
    if "classifier" not in name:
        param.requires_grad = False
```

### pipeline() vs Manual Tokenizer+Model
| Need | Use |
|---|---|
| Quick inference, default pre/post-processing OK | `pipeline("sentiment-analysis")` |
| Custom truncation/padding/max_length | Manual AutoTokenizer + AutoModel |
| Access to raw logits (pre-softmax) | Manual AutoTokenizer + AutoModel |
| Fine-tuning a model | Trainer API (still built on AutoTokenizer/AutoModel) |

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification
tok = AutoTokenizer.from_pretrained("bert-base-uncased")
model = AutoModelForSequenceClassification.from_pretrained("bert-base-uncased")
inputs = tok(text, truncation=True, max_length=128, padding=True, return_tensors="pt")
logits = model(**inputs).logits
```

### TrainingArguments Key Defaults
| Argument | Default |
|---|---|
| learning_rate | 5e-05 |
| num_train_epochs | 3 |
| per_device_train_batch_size | 8 |

### datasets Library
```python
from datasets import load_dataset
ds = load_dataset("glue", "sst2")
ds = ds.map(lambda x: tok(x["sentence"], truncation=True), batched=True)
```
Use `batched=True` for speed — processes multiple rows per call.

### Exam Traps
- Assuming "more fine-tuning = always better" — wrong with small datasets (overfitting).
- Pairing wrong Auto class with checkpoint architecture (e.g., AutoModelForCausalLM on BERT).
- Using pipeline() when raw logits or custom tokenization control is required.
- Mixing tokenizer and model from different checkpoints.
