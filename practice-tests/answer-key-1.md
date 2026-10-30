# Answer Key — Practice Test 1

**Q1. Correct: D**

No labeled outcomes exist and the goal is to discover natural groupings in the data, which is exactly what unsupervised clustering algorithms (e.g., k-means) are designed to do.

---

**Q2. Correct: A**

The agent learns through trial-and-error interaction with an environment, receiving reward or penalty signals after actions, which is the defining characteristic of reinforcement learning.

---

**Q3. Correct: A**

Raw collected data must be cleaned, transformed, and engineered into usable features before it can be fed into a model for training; this is the standard next step in the ML workflow.

---

**Q4. Correct: B**

The feedback loop is the architectural component that captures outcomes of model usage (clicks, purchases, corrections) and routes them back into the pipeline to improve future model versions.

---

**Q5. Correct: D**

The serving layer is specifically responsible for exposing a trained model as an accessible endpoint (API) and handling real-time inference requests with low latency.

---

**Q6. Correct: A**

The data layer handles collection, cleaning, transformation, and storage of data so it is in a usable state for both model training and inference.

---

**Q7. Correct: B**

The feedback loop continuously monitors model outcomes against real-world results and triggers retraining when performance metrics degrade, closing the loop between deployment and improvement.

---

**Q8. Correct: B**

The model layer encompasses training, versioning, and hosting the algorithm itself, while the serving layer is the deployment mechanism that makes the trained model accessible to applications for real-time or batch inference.

---

**Q9. Correct: B**

The widening gap between training and validation accuracy combined with declining validation performance is the signature of overfitting; dropout adds stochastic regularization and early stopping halts training at the point of best generalization.

---

**Q10. Correct: B**

Softmax converts raw output scores into a probability distribution across all 10 mutually exclusive classes that sums to 1, which is required for single-label multi-class classification.

---

**Q11. Correct: A**

Adam combines momentum with adaptive per-parameter learning rates derived from first and second moment estimates of the gradients, making it well suited for sparse gradients and noisy loss surfaces.

---

**Q12. Correct: C**

Binary Cross-Entropy is mathematically aligned with a single sigmoid output, penalizing confident wrong predictions heavily and providing well-behaved gradients for two-class problems.

---

**Q13. Correct: C**

A learning rate that is too high causes weight updates to overshoot the loss minimum repeatedly, producing oscillating or diverging loss; lowering the learning rate allows the optimizer to take smaller, more stable steps toward convergence.

---

**Q14. Correct: C**

Vanishing gradients occur when backpropagated error signals shrink exponentially as they pass through many layers of saturating activation functions like sigmoid, causing early-layer weights to receive negligible updates.

---

**Q15. Correct: C**

A large and widening gap between training and validation accuracy is the classic signature of overfitting, where the model memorizes training data instead of generalizing. Dropout randomly deactivates neurons during training, and L2 regularization penalizes large weights, both of which reduce the model's capacity to memorize noise and improve generalization.

---

**Q16. Correct: A**

CNNs use convolutional filters and pooling layers that preserve and exploit spatial relationships between pixels, making them the standard architecture for image classification and defect detection tasks.

---

**Q17. Correct: B**

RNNs, especially LSTM variants, maintain an internal hidden state that captures temporal dependencies across sequential inputs, making them well suited for time-series forecasting tasks like stock price prediction.

---

**Q18. Correct: A**

Pooling layers (such as max pooling) downsample feature maps, reducing spatial dimensions and computational load while retaining the most salient features, which also helps make the network more robust to small translations in the input.

---

**Q19. Correct: C**

RAG retrieves up-to-date external documents at inference time and injects them into the context window, so the model's answers reflect current information without any retraining.

---

**Q20. Correct: D**

The context window is a fixed architectural limit; when input exceeds it, the oldest tokens (often earliest conversation turns) are truncated or dropped so the remaining input fits, which can cause the model to 'forget' earlier context.

---

**Q21. Correct: D**

Fine-tuning adjusts the model's weights on domain-specific examples, embedding consistent jargon, tone, and formatting directly into the model's behavior for every response.

---

**Q22. Correct: A**

Self-attention computes query-key dot products to produce relevance weights for every token pair, then uses those weights to form a weighted sum of value vectors, letting each token dynamically attend to the most relevant parts of the sequence.

---

**Q23. Correct: D**

RAG retrieves relevant document chunks from a vector store at query time and grounds the generated answer in them, enabling accurate source citation and reducing hallucination, without needing retraining.

---

**Q24. Correct: B**

Embeddings map text into dense numeric vectors such that semantically similar text produces vectors that are close together in vector space, enabling similarity search like cosine similarity.

---

**Q25. Correct: A**

Chain-of-thought prompting instructs the model to break down the problem into intermediate reasoning steps, which has been shown to significantly improve accuracy on multi-step arithmetic and logic tasks.

---

**Q26. Correct: A**

Guidance scale controls how strongly the diffusion process is steered toward the text prompt; increasing it makes outputs adhere more closely to the prompt but reduces variation and can introduce artifacts at extreme values.

---

**Q27. Correct: C**

BPE splits rare/unknown words into known subword units (e.g., 'cardio' + 'myopathy'), so the model can represent and learn from them without an out-of-vocabulary token.

---

**Q28. Correct: B**

NER is specifically designed to identify and classify spans of text into predefined categories like PERSON, ORG, and DATE, matching the firm's requirement exactly.

---

**Q29. Correct: C**

Dense embeddings place semantically similar words/phrases near each other in vector space, so synonyms and related concepts yield high similarity scores even without exact word overlap.

---

**Q30. Correct: D**

Including bigrams preserves the pairing of 'not' with 'good' as a single feature, and retaining negation words ensures the classifier can distinguish negated sentiment from positive sentiment.

---

**Q31. Correct: B**

Stemming applies heuristic suffix-stripping rules (e.g., 'running' -> 'runn'), which can produce non-words, while lemmatization uses a dictionary and part-of-speech context to return the correct base form (e.g., 'running' -> 'run').

---

**Q32. Correct: D**

Fine-tuning a pretrained transformer leverages existing language knowledge, requiring far fewer labeled examples and less training time to achieve high accuracy than training from scratch.

---

**Q33. Correct: C**

Transformer-based contextual embeddings (e.g., BERT-style models) compute a word's vector dynamically based on its surrounding tokens via self-attention, so 'bank' in a financial context gets a different embedding than 'bank' in a geographical context. This directly solves the word-sense disambiguation problem that static embeddings cannot handle.

---

**Q34. Correct: A**

The pipeline() abstraction bundles tokenizer, model, and post-processing into a single call, letting the developer get predictions with one line of code and no training.

---

**Q35. Correct: B**

AutoTokenizer.from_pretrained() inspects the checkpoint's configuration and automatically instantiates the matching tokenizer class, removing the need to know the exact architecture in advance.

---

**Q36. Correct: C**

num_train_epochs sets the number of complete passes over the training dataset, directly controlling training duration and the amount the model sees the data.

---

**Q37. Correct: D**

Fine-tuning a pretrained model transfers general language knowledge learned from massive pretraining corpora, requiring far fewer labeled examples and far less compute to reach strong task-specific performance.

---

**Q38. Correct: C**

The tokenizer splits text into tokens, maps them to vocabulary IDs, and produces attention masks and other inputs the model's forward pass requires — it is the bridge between raw text and model input tensors.

---

**Q39. Correct: B**

The Model Hub is the centralized repository where pretrained checkpoints are published, tagged by task/language/license, and can be searched and loaded directly via from_pretrained() using their repo ID.

---

**Q40. Correct: C**

Setting padding=True pads all sequences in a batch to the same length so tensors can be stacked, truncation=True caps overly long tickets at max_length=128 to control memory and compute, and this combination is the standard pattern used with Trainer for variable-length text classification.

---

**Q41. Correct: D**

Gradio's ChatInterface and Blocks natively support generator functions that yield partial outputs, which Gradio streams to the UI token-by-token, producing a real-time typing effect for chatbot responses.

---

**Q42. Correct: D**

st.spinner (or st.progress) gives users explicit visual feedback during long-running operations, which is the standard UX pattern for inference latency in Streamlit apps and directly addresses the perceived-freeze problem.

---

**Q43. Correct: D**

gr.Label is purpose-built for classification outputs: it renders class names alongside confidence percentages in a visually ranked list, which is the standard component for this use case.

---

**Q44. Correct: A**

share=True tells Gradio to create a temporary public URL (via Gradio's tunneling service) so the app can be accessed outside the local network, commonly used for quick demos.

---

**Q45. Correct: A**

Streamlit's execution model reruns the full Python script from top to bottom whenever a widget value changes, whereas Gradio binds specific functions to specific component events (e.g., a button click triggers only its linked callback), which is a core architectural distinction tested on the exam.

---

**Q46. Correct: B**

Wrapping the model in a lightweight API framework and containerizing it with Docker creates a consistent, portable, scalable unit that can be deployed identically across dev, staging, and production, and it exposes a clean interface for the web app to consume.

---

**Q47. Correct: C**

Gradual accuracy degradation with no code changes is a classic sign of data drift, where real-world input data shifts away from the distribution the model was trained on. Monitoring input feature distributions over time catches this before accuracy visibly suffers.

---

**Q48. Correct: D**

A model card translates technical model details into clear, structured, non-technical language covering purpose, performance, limitations, and intended use, which is exactly what business stakeholders need to make an informed approval decision.

---

