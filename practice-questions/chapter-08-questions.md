## Chapter 8: Transfer Learning in Practice with the Hugging Face Ecosystem — Practice Questions

**Q1.** A team has only 400 labeled examples for a niche legal-document classification task and limited GPU access (single T4 GPU, 2 hours/week budget). They start from bert-base-uncased. Which approach is BEST to avoid overfitting while fitting the compute budget?

A) Freeze the pretrained encoder layers and train only a new classification head on top
B) Fully fine-tune all 110M parameters for 20 epochs with a high learning rate
C) Train a transformer from random initialization on the 400 examples
D) Fully fine-tune all layers but reduce the dataset to 40 examples to speed up training

<details>
<summary>Answer</summary>

**Correct: A**

Small dataset + limited compute means freezing the encoder and only updating a lightweight head drastically reduces trainable parameters and overfitting risk while still leveraging pretrained representations.

**Why the others are wrong:**
- Full fine-tuning of 110M params on 400 examples causes severe overfitting; a high learning rate also destroys pretrained weights.
- Discards all transfer learning benefit; random init needs orders of magnitude more data to converge.
- Shrinking the dataset while fully fine-tuning makes overfitting worse, not better.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A company has 600,000 labeled support tickets and a dedicated 8-GPU A100 cluster. They need maximum accuracy for ticket-priority classification. Which strategy is BEST?

A) Freeze all pretrained layers and only train the classification head
B) Use the pipeline API in zero-shot mode without any training
C) Freeze everything except the embedding layer only
D) Fully fine-tune all layers of the pretrained model with a small learning rate (e.g., 2e-5)

<details>
<summary>Answer</summary>

**Correct: D**

A large labeled dataset plus ample compute means full fine-tuning yields the best accuracy since overfitting risk is low and every layer can adapt to task-specific patterns.

**Why the others are wrong:**
- Freezing everything underutilizes the available data and compute, leaving accuracy on the table.
- Zero-shot ignores the 600k labeled examples entirely.
- Freezing everything except embeddings rarely helps — higher task-relevant layers never adapt.

</details>

---

**Q3.** You need to run inference on 2 million sentences, with custom truncation to 128 tokens, dynamic padding, and you must inspect raw pre-softmax logits to apply a custom calibrated threshold before storing results. Which workflow should you use?

A) AutoTokenizer and AutoModel loaded manually, with explicit tokenizer and model calls
B) The transformers pipeline() API with default settings
C) The Trainer API's predict() method only, without a tokenizer
D) The datasets library's map() function with no model involved

<details>
<summary>Answer</summary>

**Correct: A**

Manual tokenizer+model usage gives full control over tokenization parameters and direct access to raw logits; pipeline() hides these details and applies its own post-processing.

**Why the others are wrong:**
- pipeline() uses default tokenization settings and typically returns post-processed scores, not raw logits.
- Trainer.predict() still requires a tokenizer/model already configured and is not a minimal manual workflow.
- datasets.map() alone performs no model inference.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** You load the checkpoint 't5-small' to build an abstractive summarization model. Which AutoModel class correctly pairs with this checkpoint?

A) AutoModelForCausalLM
B) AutoModelForSeq2SeqLM
C) AutoModelForMaskedLM
D) AutoModelForSequenceClassification

<details>
<summary>Answer</summary>

**Correct: B**

T5 is an encoder-decoder (sequence-to-sequence) architecture, so AutoModelForSeq2SeqLM is the correct class for generation tasks like summarization.

**Why the others are wrong:**
- AutoModelForCausalLM is for decoder-only models like GPT-2.
- AutoModelForMaskedLM is for encoder-only MLM models like BERT.
- AutoModelForSequenceClassification adds a classification head, not suited for text generation.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** Which combination correctly loads a matching tokenizer and model for the checkpoint 'bert-base-uncased' for a binary sentiment classification fine-tuning task?

A) AutoTokenizer.from_pretrained('bert-base-uncased') with AutoModelForSequenceClassification.from_pretrained('bert-base-uncased')
B) AutoTokenizer.from_pretrained('gpt2') with AutoModelForSequenceClassification.from_pretrained('bert-base-uncased')
C) AutoTokenizer.from_pretrained('bert-base-uncased') with AutoModelForCausalLM.from_pretrained('bert-base-uncased')
D) AutoTokenizer.from_pretrained('bert-base-uncased') with AutoModelForQuestionAnswering.from_pretrained('bert-base-uncased')

<details>
<summary>Answer</summary>

**Correct: A**

The tokenizer and model checkpoint names must match (same vocabulary/tokenization scheme), and AutoModelForSequenceClassification is the correct head for classification tasks.

**Why the others are wrong:**
- A gpt2 tokenizer uses a different vocabulary/byte-pair encoding, corrupting input IDs for a BERT model.
- AutoModelForCausalLM wraps BERT with an inappropriate causal LM head since BERT is not autoregressive.
- AutoModelForQuestionAnswering adds a span-extraction head, not suited for sentiment classification.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** You instantiate TrainingArguments() without specifying learning_rate. What learning rate does the Trainer API use by default?

A) 1e-3
B) 0.01
C) 5e-5
D) 3e-4

<details>
<summary>Answer</summary>

**Correct: C**

5e-05 is the documented default learning_rate value in transformers.TrainingArguments.

**Why the others are wrong:**
- 1e-3 is a common default for optimizers training from scratch, not the Trainer default for fine-tuning.
- 0.01 is far too high for fine-tuning a pretrained transformer and would destroy pretrained weights.
- 3e-4 is a commonly cited rate in other frameworks but not the Trainer API default.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** Which code snippet correctly freezes all parameters of a Hugging Face model's base encoder while keeping the classification head trainable?

A) model.freeze()
B) for param in model.parameters(): param.requires_grad = True
C) for name, param in model.named_parameters(): if 'classifier' not in name: param.requires_grad = False
D) model.eval()

<details>
<summary>Answer</summary>

**Correct: C**

Iterating over named_parameters and disabling gradients for all parameters outside the classification head is the standard PyTorch pattern for partial fine-tuning.

**Why the others are wrong:**
- model.freeze() is not a method on Hugging Face PyTorch models.
- Setting requires_grad = True for everything is the opposite of freezing.
- model.eval() only changes dropout/batchnorm behavior for inference; it does not disable gradient updates.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** What fundamentally distinguishes transfer learning from training a model from scratch?

A) Transfer learning initializes model weights from a model already trained on another task/dataset, rather than random initialization
B) Transfer learning always uses a smaller model architecture
C) Transfer learning never updates any weights during training
D) Transfer learning requires no labeled data at all

<details>
<summary>Answer</summary>

**Correct: A**

The defining property of transfer learning is reusing weights learned on a source task as the starting point, enabling faster convergence and better performance with less target-task data.

**Why the others are wrong:**
- Architecture size is unrelated to whether a model uses transfer learning.
- Weights can still be updated during fine-tuning; frozen weights describe only one specific strategy, not the general definition.
- Zero-shot inference needs no labeled data, but that's a specific use case, not the definition of transfer learning.

</details>

---

