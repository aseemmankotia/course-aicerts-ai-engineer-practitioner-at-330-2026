# Practice Test 2: AI+ Engineer Practitioner AT-330: Exam Prep Masterclass

- **Questions:** 48
- **Time limit:** 90 minutes
- **Passing score:** 70%%

> Answers are in `answer-key-2.md`. Track results in `score-tracker.md`.

---

**Q1.** A payments company has 2 million transaction records. Only 3% are manually labeled as 'fraud' or 'legitimate' by analysts; the remaining 97% have no label at all, and getting more labels is too expensive to scale. The team wants to build a model that uses the small labeled set to guide learning from the much larger unlabeled set. Which ML paradigm BEST fits this scenario?

A) Semi-supervised learning, since a small labeled subset guides pattern discovery across the larger unlabeled dataset
B) Reinforcement learning, since the model can be rewarded for correctly flagging fraud over time
C) Pure supervised learning restricted to the 3% labeled subset, discarding the unlabeled data
D) Unsupervised clustering only, since labels are too sparse to be useful

---

**Q2.** A robotics team is training a warehouse arm to stack boxes. There is no dataset of 'correct' grasp actions — instead, the arm tries different grips and receives a score only after the full stack either falls or succeeds, often many steps after the critical action occurred. Which statement correctly identifies the paradigm and its core challenge?

A) This is reinforcement learning, and the core challenge is credit assignment — determining which earlier action caused the delayed reward
B) This is supervised learning, and the core challenge is insufficient labeled training examples of correct grips
C) This is unsupervised learning, and the core challenge is choosing the right number of clusters to represent grip types
D) This is reinforcement learning, and the core challenge is feature scaling across sensor inputs

---

**Q3.** During the ML workflow, a data scientist tunes model hyperparameters by repeatedly checking performance against the same held-out dataset until accuracy stops improving, then reports that same dataset's score as the final expected real-world performance. What is wrong with this workflow?

A) The model was never trained, so no performance can be measured at all
B) The dataset used for tuning became a test set substitute, so reported performance is optimistically biased and a separate untouched test set should have been used for the final evaluation
C) Hyperparameter tuning should only ever be done on the training set, never on any held-out data
D) Nothing is wrong; using the same held-out set for tuning and final reporting is the standard, unbiased approach

---

**Q4.** A fraud-detection model has been running in production for three months. Infrastructure logs show zero errors and normal latency, but the precision of fraud flags has steadily declined. Which architectural addition would BEST address this issue?

A) Add more compute resources to the serving layer to handle increased load
B) Increase the size of the underlying model to improve its capacity
C) Implement a feedback loop that compares live predictions against ground-truth outcomes to detect concept drift
D) Add a caching layer in front of the inference endpoint to reduce response time

---

**Q5.** Which layer in a standard AI system architecture is responsible for ingestion, cleaning, feature transformation, and schema validation BEFORE information reaches the model for training or inference?

A) Serving layer
B) Model layer
C) Data layer
D) Feedback layer

---

**Q6.** A team is designing the serving layer for a customer support chatbot powered by an LLM. Traffic is highly variable, spiking during business hours and dropping to near-zero overnight. Cost efficiency and automatic scaling are top priorities. Which serving configuration BEST meets these requirements?

A) A fixed-capacity VM cluster that runs continuously at a size set for peak load
B) A serverless, autoscaling inference endpoint that can scale to zero during idle periods
C) A dedicated GPU cluster scaled manually on a fixed weekly schedule
D) A nightly batch job that processes all accumulated chat requests at once

---

**Q7.** In the AT-330 end-to-end AI architecture model, what is the PRIMARY distinction between the model layer and the serving layer?

A) The model layer stores raw, unprocessed data while the serving layer stores cleaned, feature-engineered data
B) The model layer encompasses training, versioning, and artifact storage, while the serving layer exposes the trained model for inference through endpoints or APIs
C) The model layer and serving layer are interchangeable terms describing the same component in different documentation
D) The model layer manages the user-facing interface while the serving layer manages human data-labeling workflows

---

**Q8.** A hospital is building an AI system that must deliver real-time inference for ICU alerts, run weekly batch retraining on newly collected patient data, and maintain a complete audit trail of every prediction for compliance. Which end-to-end architecture BEST satisfies ALL of these requirements?

A) A single monolithic application combining training code and inference code deployed as one unit
B) A batch-only architecture that processes all ICU data once per day and generates delayed alerts
C) A versioned data pipeline in the data layer feeding a model layer with separate real-time inference and batch-retraining components, combined with a feedback loop that logs every prediction's inputs and outputs for traceability
D) A real-time inference-only setup where a data scientist manually retrains the model whenever performance seems to degrade

---

**Q9.** A deep feedforward network with 10 hidden layers uses sigmoid activation throughout. After several epochs, the loss plateaus almost immediately and weight updates in the first few layers are nearly zero while later layers still update slightly. What is the BEST fix for this training stall?

A) Increase the learning rate significantly to force larger weight updates
B) Add more hidden layers to increase model capacity
C) Switch the loss function from cross-entropy to mean squared error
D) Replace sigmoid activation functions in the hidden layers with ReLU

---

**Q10.** A 5-layer dense network reaches 98% training accuracy but only 68% validation accuracy, and the gap widens each epoch. No regularization is currently applied. Which action BEST addresses this while preserving model capacity?

A) Add dropout layers between the dense layers with an appropriate dropout rate
B) Increase the number of training epochs to let the model converge further
C) Remove the validation set so training can use more data
D) Increase the batch size to equal the full training set size

---

**Q11.** A network performs binary classification (spam vs. not spam) with a single output neuron. Which output activation and loss function pairing is correct for this task?

A) Softmax output activation with sparse categorical cross-entropy loss
B) ReLU output activation with mean squared error loss
C) Sigmoid output activation with binary cross-entropy loss
D) Linear (identity) output activation with hinge loss

---

**Q12.** A deep network is trained with the Adam optimizer using a learning rate of 0.01. After a few epochs, the training loss oscillates wildly and then becomes NaN. Which change is the BEST first step to fix this instability?

A) Increase the learning rate to help the optimizer escape local minima
B) Switch the loss function to mean absolute error
C) Decrease the learning rate and/or apply gradient clipping
D) Remove the bias terms from all layers

---

**Q13.** Why can a single-layer perceptron (with no hidden layer) never learn the XOR function regardless of training time or learning rate?

A) XOR is not linearly separable, and a single-layer perceptron can only represent linear decision boundaries
B) XOR requires more than two binary input features to be learnable
C) XOR requires a nonlinear activation such as softmax in the output layer
D) The perceptron learning rule does not mathematically converge for binary-valued inputs

---

**Q14.** An RNN is trained on long sequences using backpropagation through time. During training, gradient norms grow extremely large over successive timesteps and the loss eventually becomes NaN. Which technique BEST addresses this specific instability?

A) Increase the sequence length to give the model more context
B) Switch to a much larger batch size
C) Apply gradient clipping to cap the gradient norm during backpropagation
D) Reduce the number of training epochs

---

**Q15.** A classification network's training loss steadily decreases over 50 epochs, but validation loss decreases until epoch 12 then rises continuously while validation accuracy plateaus. Which single action BEST addresses this behavior?

A) Increase the learning rate to help the optimizer escape the current local minimum faster
B) Add two more hidden layers to give the network more representational capacity
C) Replace the categorical cross-entropy loss with mean squared error to smooth the loss landscape
D) Apply dropout and L2 weight regularization, and retrain using early stopping based on validation loss

---

**Q16.** A language model must generate coherent text where pronoun resolution depends on context introduced 150+ tokens earlier in the paragraph. During training, a vanilla RNN baseline fails to learn this dependency despite many epochs. Which architecture BEST resolves this specific failure?

A) A simple feedforward network using a fixed-size sliding window of the last 10 tokens
B) A single 1D convolutional layer with a kernel size of 3 applied over the token embeddings
C) An LSTM network with input, forget, and output gates controlling a dedicated cell state
D) A deeper vanilla RNN with more hidden layers stacked on top of each other

---

**Q17.** An autonomous vehicle perception system must detect pedestrians, vehicles, and traffic signs in a single camera frame with end-to-end inference latency under 50ms on embedded hardware. Which approach BEST meets these requirements?

A) A two-stage detector using a Region Proposal Network followed by a separate classification CNN (Faster R-CNN style)
B) A single-stage detector that predicts bounding boxes and class probabilities in one forward pass (YOLO-style)
C) A sliding-window classifier that manually scans the image at multiple scales using hand-crafted HOG features
D) A recurrent network that sequentially scans image patches left-to-right and classifies each patch independently

---

**Q18.** A CNN layer receives an input feature map of size 32x32 with a single channel. It applies 16 filters of size 5x5, stride 1, and zero padding of 0. What is the spatial size (height x width) of the output feature map?

A) 28x28
B) 32x32
C) 27x27
D) 30x30

---

**Q19.** A company built a chatbot using an LLM with a 4,096-token context window. Users report that increasing conversation history beyond roughly 3,000 tokens causes a dramatic slowdown in response time and higher API costs, even though the token count stays within the context limit. What is the technical reason for this?

A) The tokenizer fails to encode conversations longer than 3,000 tokens
B) Self-attention computation scales quadratically (O(n^2)) with sequence length, so cost and latency grow faster than token count
C) The LLM automatically fine-tunes on each new conversation, adding overhead
D) Context windows degrade token embeddings linearly, causing slow decoding

---

**Q20.** A legal tech startup wants an LLM to generate court-ready legal briefs in the style of a specific law firm, using a proprietary corpus of 5,000 previously filed briefs. The team has a limited compute budget and wants to preserve the base model's general language capabilities while specializing it for this narrow task. Which approach BEST meets these requirements?

A) Pretrain a new LLM from scratch using only the 5,000 briefs
B) Use prompt engineering only, inserting the 5,000 briefs as few-shot examples in every prompt
C) Increase the base model's context window so all 5,000 briefs fit into a single prompt
D) Apply parameter-efficient fine-tuning (e.g., LoRA) on top of a pretrained base model using the 5,000 briefs

---

**Q21.** Which subword tokenization algorithm is used by GPT-style LLMs to balance vocabulary size with the ability to represent rare or out-of-vocabulary words, by iteratively merging the most frequent pairs of characters or byte sequences?

A) Byte-Pair Encoding (BPE)
B) WordPiece
C) Character-level tokenization
D) Whole-word tokenization

---

**Q22.** An LLM confidently generates a fabricated citation to a nonexistent academic paper when asked to support a claim. Which inherent characteristic of LLMs BEST explains this failure mode?

A) LLMs generate text by predicting statistically likely token sequences, not by verifying facts against ground truth
B) LLMs retrieve answers from a verified knowledge base and occasionally index entries incorrectly
C) LLMs intentionally deceive users when training data is incomplete
D) LLMs only hallucinate when the context window limit has been exceeded

---

**Q23.** A legal-tech company built a RAG chatbot over case law documents. Documents are chunked at 500 tokens with 50-token overlap, and retrieval logs confirm the top-5 returned passages are consistently relevant to each query. Despite this, users report the bot confidently cites case numbers that do not exist in any source document. What is the BEST next step to reduce these fabricated citations?

A) Increase chunk size to 2000 tokens to give the model more surrounding context
B) Switch to a larger generative model with more parameters
C) Increase top-k retrieval from 5 to 20 passages
D) Add an explicit grounding instruction requiring the model to cite only information present in the retrieved passages, and verify generated citations against retrieved source metadata

---

**Q24.** A team is building semantic search over product descriptions using dense embedding vectors stored in a vector database. Their embedding model does NOT normalize output vectors to unit length. Which similarity metric should they use to ensure accurate semantic ranking that is not skewed by differences in vector magnitude?

A) Euclidean (L2) distance
B) Raw dot product
C) Jaccard similarity
D) Cosine similarity

---

**Q25.** A product team using a text-to-image diffusion pipeline wants output images to adhere MORE strictly to the text prompt, even if it means reduced image diversity and occasional visual artifacts. Which parameter should they increase?

A) Classifier-free guidance (CFG) scale
B) Number of denoising/inference steps
C) Random seed value
D) Output image resolution

---

**Q26.** A company's internal knowledge base (pricing and inventory levels) changes daily. They need a GenAI assistant that always reflects current data without expensive or frequent retraining cycles. Which architectural approach BEST meets this requirement?

A) Implement RAG: store current data in a retrievable knowledge store and inject relevant results into the prompt at query time
B) Fine-tune the LLM every night on the latest data snapshot
C) Rely on prompt engineering alone with a static system prompt listing key facts
D) Switch to a larger foundation model with more parameters

---

**Q27.** A healthcare NLP team is normalizing clinical notes before feeding them into a classifier. They need 'running', 'ran', and 'runs' to map to the dictionary base form 'run', and critically need 'better' to map to 'good' rather than being crudely truncated. Which preprocessing technique BEST satisfies both requirements?

A) Stemming using the Porter algorithm
B) Simple whitespace tokenization
C) Stop word removal followed by n-gram generation
D) Lemmatization using a vocabulary and morphological analysis

---

**Q28.** An engineer is building a search system that must distinguish 'bank' (financial institution) from 'bank' (river edge) based on surrounding words in each sentence. Which embedding approach is required to produce DIFFERENT vector representations for the same word depending on context?

A) One-hot encoded vectors
B) Static Word2Vec embeddings
C) TF-IDF weighted vectors
D) Contextual embeddings from a transformer encoder (e.g., BERT)

---

**Q29.** In a BIO tagging scheme used for Named Entity Recognition, a token sequence is labeled B-ORG, I-ORG, I-ORG. What does the 'I-ORG' label indicate on the second and third tokens?

A) The token marks the start of a brand new ORG entity
B) The token continues the same multi-token ORG entity started by the preceding B-ORG
C) The token is outside any named entity
D) The token indicates a tagging error and should be discarded

---

**Q30.** A product review states: 'The battery life is terrible but the camera is excellent.' A document-level sentiment classifier scores this review as neutral, which loses valuable per-feature insight. Which technique should be applied to correctly capture that battery life is negative while camera is positive within the same review?

A) Binary sentiment classification with a higher confidence threshold
B) Bag-of-words frequency counting of positive and negative words
C) Document-level sentiment classification with a larger training set
D) Aspect-Based Sentiment Analysis (ABSA) extracting sentiment per identified aspect term

---

**Q31.** GPT-style transformer models need to handle rare and previously unseen words (e.g., 'unbelievability') without an explicit entry in the vocabulary. Which tokenization strategy accomplishes this by iteratively merging the most frequent character/subword pairs into a fixed-size subword vocabulary?

A) Fixed whole-word tokenization with an out-of-vocabulary token
B) Character-level tokenization with no merging
C) Whitespace-only tokenization
D) Byte Pair Encoding (BPE)

---

**Q32.** What is the computational complexity of the self-attention mechanism in a standard Transformer with respect to input sequence length n?

A) O(n^2)
B) O(log n)
C) O(n)
D) O(n^3)

---

**Q33.** A legal-tech company is building a clause-classification system. Their corpus contains many instances of the word "discharge" used with different meanings depending on context (e.g., discharge of debt vs. discharge of an employee). The current model, which uses one fixed vector per unique word regardless of surrounding text, misclassifies these clauses because it cannot distinguish the senses. Which change to the text representation approach BEST resolves this issue?

A) Increase the n-gram range in a TF-IDF vectorizer to capture longer phrases
B) Switch from TF-IDF to one-hot encoding with a larger vocabulary size
C) Replace the static word embeddings with contextual embeddings generated by a transformer encoder like BERT
D) Apply stemming more aggressively before generating Word2Vec embeddings

---

**Q34.** A team is fine-tuning a 7B-parameter causal language model on a single 24GB GPU. Full fine-tuning causes out-of-memory errors even at batch size 1. They need to adapt the model to a new domain without retraining all parameters. Which approach BEST meets this requirement?

A) Reduce the sequence length to 32 tokens and perform full fine-tuning
B) Switch to gradient descent with a larger learning rate to converge faster with fewer steps
C) Apply LoRA via the PEFT library to inject trainable low-rank adapters while freezing the base weights
D) Quantize the tokenizer vocabulary to reduce embedding matrix size

---

**Q35.** A developer loads a model with AutoModelForSequenceClassification.from_pretrained('bert-base-uncased') but tokenizes input text using a tokenizer loaded from a different checkpoint, 'roberta-base'. What is the MOST likely consequence?

A) Token IDs produced by the RoBERTa tokenizer will not correspond to BERT's vocabulary, corrupting the embeddings the model receives
B) The model will automatically detect the mismatch and switch to the correct tokenizer
C) Training will run normally since all Hugging Face tokenizers share the same vocabulary
D) The pipeline will throw a compile-time error before any code executes

---

**Q36.** When batching variable-length sequences for training with the Trainer API, which configuration correctly implements dynamic padding so each batch is padded only to its own longest sequence rather than a fixed maximum length?

A) Set tokenizer(text, padding='max_length', max_length=512) for every example
B) Set per_device_train_batch_size=1 to avoid needing padding at all
C) Manually pad all sequences to the model's absolute maximum position embeddings
D) Pass a DataCollatorWithPadding instance as the data_collator argument to Trainer

---

**Q37.** A fine-tuned checkpoint was originally trained with 3 output labels, but a new task requires reusing its encoder weights with 5 output labels. Loading it directly with AutoModelForSequenceClassification.from_pretrained(checkpoint, num_labels=5) raises a size mismatch error on the classification head. Which parameter resolves this while preserving the reusable encoder weights?

A) revision='main'
B) trust_remote_code=True
C) ignore_mismatched_sizes=True
D) output_hidden_states=True

---

**Q38.** A team needs to classify customer support tickets into categories that were not known at training time and have no labeled examples, using only a list of candidate category names provided at inference. Which Hugging Face pipeline task is purpose-built for this?

A) text-classification
B) feature-extraction
C) fill-mask
D) zero-shot-classification

---

**Q39.** After fine-tuning a model, a developer calls model.push_to_hub('my-org/my-model') and tokenizer.push_to_hub('my-org/my-model'). What is the PRIMARY effect of these calls?

A) The model is permanently deleted from local disk after upload to save space
B) The model weights, config, and tokenizer files are uploaded to a new or existing repository on the Hugging Face Hub, making them loadable via from_pretrained
C) The model is automatically converted to ONNX format before being hosted for inference
D) The training logs and optimizer state are uploaded so training can resume on any machine without checkpoints

---

**Q40.** A team fine-tunes GPT-2 (a causal language model) for a text classification task using Hugging Face Transformers. During training, the Trainer throws an error because the tokenizer has no padding token defined, causing batch collation to fail when sequences in a batch have different lengths. The team needs a fix that preserves the model's existing vocabulary and embedding matrix size while allowing dynamic padding in batches. Which solution BEST meets this requirement?

A) Resize the model's token embeddings to add a new [PAD] token and retrain the embedding layer from scratch
B) Set tokenizer.pad_token = tokenizer.eos_token so the existing end-of-sequence token is reused for padding, with attention masks still applied correctly
C) Switch the base model to BERT, since BERT tokenizers include a native [PAD] token by default
D) Disable padding entirely and truncate every sequence in the dataset to a single fixed length before training

---

**Q41.** A customer-facing GenAI chatbot UI must display the LLM's response progressively, token-by-token, as it is generated, rather than showing nothing until the full answer is ready. Which implementation BEST meets this requirement in a Gradio-based app?

A) Call the model synchronously, store the full string, and render it once generation completes
B) Build the response handler as a Python generator function using 'yield' so Gradio streams partial outputs to the component as they arrive
C) Poll a REST endpoint on a 5-second interval from client-side JavaScript to fetch the current response buffer
D) Render the output inside a static HTML <iframe> that is manually refreshed by the user

---

**Q42.** Users of an AI image-captioning web app report that the interface appears frozen during the model's 8-second inference time, leading to repeated accidental double-submissions. Which UX fix BEST addresses this issue?

A) Remove the submit button entirely so users cannot trigger duplicate requests
B) Display a progress indicator or spinner and disable the submit control while inference is running
C) Reduce the client-side request timeout to 1 second so failed calls return faster
D) Cache and return results from unrelated prior requests to always provide an immediate response

---

**Q43.** A team needs to build an internal analytics tool with a persistent sidebar, multiple distinct pages, and several linked widgets (sliders, dropdowns, filters) for exploring tabular data alongside model predictions, with heavy emphasis on custom page layout. Which framework choice BEST fits these requirements?

A) A single Gradio Blocks interface, since Blocks supports arbitrary component nesting
B) Streamlit, due to its native multipage app structure, sidebar API, and flexible layout primitives
C) Plain Flask with Jinja2 templates and no front-end framework
D) Exporting Jupyter widgets as static HTML for deployment

---

**Q44.** A Gradio app serving a single-instance LLM experiences request pileup and crashes when multiple users submit prompts simultaneously, because the model can only safely process one inference at a time. Which configuration change BEST resolves this without adding external infrastructure?

A) Set share=True when launching the app to generate a public link
B) Enable Gradio's queue() mechanism with a concurrency_limit set to match the model's safe throughput
C) Increase the server_port number used by the app
D) Disable all client-side caching in the browser

---

**Q45.** A production chat GUI exposes a fine-tuned LLM to end users. To reduce the risk of prompt injection attacks overriding the system's hidden instructions, which architecture/UX practice is MOST critical?

A) Keeping user input strictly separated from the system prompt, and validating/sanitizing user input before it is concatenated into the final prompt sent to the model
B) Allowing users to directly edit the system prompt field so they can customize behavior
C) Increasing the chat window font size to improve readability
D) Rendering any raw HTML submitted by users directly into the chat window without escaping

---

**Q46.** A fraud-detection model has been deployed behind a REST API for six months with stable latency, throughput, and error rates. Business stakeholders now report a sudden spike in false negatives, even though the feature pipeline and input schema have not changed. Which monitoring practice would MOST likely have caught this issue before it impacted the business?

A) Tracking API response time percentiles (p50/p95/p99)
B) Logging HTTP status codes along with container CPU and memory utilization
C) Comparing production feature and prediction distributions against the training baseline to detect data/concept drift
D) Increasing the number of replica containers behind the load balancer to handle more traffic

---

**Q47.** You are finalizing a production Dockerfile to serve a FastAPI-based inference endpoint. Which CMD instruction reflects production-ready best practice?

A) CMD ["uvicorn", "app:app", "--reload", "--host", "0.0.0.0", "--port", "8000"]
B) CMD ["python", "app.py"]
C) CMD ["gunicorn", "-w", "4", "-k", "uvicorn.workers.UvicornWorker", "app:app", "--bind", "0.0.0.0:8000"]
D) CMD ["flask", "run", "--debug"]

---

**Q48.** A team is rolling out a new recommendation model version. They route only 5% of live production traffic to the new version while monitoring click-through rate and conversion, then gradually increase the traffic share if KPIs hold steady — ready to roll back quickly if they degrade. Which deployment strategy does this describe?

A) Blue-green deployment
B) Shadow deployment
C) A/B testing with a fixed 50/50 traffic split
D) Canary deployment

---

