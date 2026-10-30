# Practice Test 1: AI+ Engineer Practitioner AT-330: Exam Prep Masterclass

- **Questions:** 48
- **Time limit:** 90 minutes
- **Passing score:** 70%%

> Answers are in `answer-key-1.md`. Track results in `score-tracker.md`.

---

**Q1.** A retail company wants to group customers into segments based on purchasing behavior without any predefined labels, in order to discover natural clusters for marketing campaigns. Which machine learning approach BEST fits this requirement?

A) Reinforcement learning with reward signals for each sale
B) Supervised learning with labeled customer segments
C) Transfer learning from a pre-trained image classifier
D) Unsupervised learning using clustering algorithms

---

**Q2.** A robotics engineer is training an agent to learn optimal navigation actions in a warehouse by giving it positive or negative feedback after each action across many trial runs, with no labeled dataset of correct moves provided upfront. Which ML paradigm is being used?

A) Reinforcement learning
B) Supervised learning
C) Unsupervised learning
D) Semi-supervised learning

---

**Q3.** In the standard machine learning workflow used in AI engineering projects, which step directly follows data collection and precedes model training?

A) Data preprocessing and feature engineering
B) Model deployment
C) Model monitoring
D) Hyperparameter tuning after training completes

---

**Q4.** A retail company deploys an AI-powered recommendation engine. Every click, purchase, and dwell-time metric from users is logged and periodically used to retrain the underlying model so recommendations improve over time. Which architectural component is responsible for capturing this user interaction data and routing it back for retraining?

A) Serving layer
B) Feedback loop
C) Model layer
D) Data layer

---

**Q5.** A team is designing an end-to-end AI application. They need a layer that accepts real-time requests from client applications and returns predictions with minimal latency. Which layer in the AI system architecture best fulfills this requirement?

A) Data layer
B) Feedback loop
C) Model layer
D) Serving layer

---

**Q6.** Which architectural layer in an AI system is responsible for ingesting raw data, cleaning it, and transforming it into a usable format before it is passed to training or inference processes?

A) Data layer
B) Model layer
C) Serving layer
D) Feedback loop

---

**Q7.** A deployed fraud-detection model's accuracy begins to drop as transaction patterns change over time. Which architectural component is responsible for monitoring this performance degradation and triggering a retraining cycle?

A) Serving layer
B) Feedback loop
C) Data layer
D) Model layer

---

**Q8.** What is the primary distinction between the model layer and the serving layer in an end-to-end AI system architecture?

A) The model layer stores raw data while the serving layer stores cleaned data
B) The model layer trains and holds the algorithm while the serving layer exposes that trained model via an endpoint for inference
C) The model layer handles user interface design while the serving layer handles backend logic
D) The model layer is used only for feedback loops while the serving layer is used only for training

---

**Q9.** A data science team trains a feedforward neural network for 200 epochs on a tabular dataset. Training accuracy reaches 99.8% but validation accuracy plateaus at 76% and then starts declining after epoch 60. Which single action BEST addresses this situation?

A) Increase the learning rate to speed up convergence past the plateau
B) Add dropout layers and apply early stopping based on validation loss
C) Remove the validation set so the model can train on all available data
D) Switch the activation function in the hidden layers from ReLU to linear

---

**Q10.** You are designing the output layer of a neural network for a 10-class image classification problem where each image belongs to exactly one class. Which activation function should be used on the output layer?

A) Sigmoid
B) Softmax
C) ReLU
D) Tanh

---

**Q11.** A model is being trained on a dataset with sparse, high-dimensional features, and the team observes that a plain Stochastic Gradient Descent optimizer converges very slowly with oscillating loss. Which optimizer should they switch to for adaptive, per-parameter learning rates?

A) Adam
B) Vanilla gradient descent with a fixed learning rate
C) Batch gradient descent without momentum
D) A larger fixed learning rate with plain SGD

---

**Q12.** Which loss function is the standard choice for a binary classification neural network whose output layer uses a single sigmoid neuron?

A) Mean Squared Error
B) Categorical Cross-Entropy
C) Binary Cross-Entropy
D) Hinge Loss

---

**Q13.** During training, the loss value oscillates wildly between epochs and occasionally spikes to very large numbers instead of steadily decreasing. Which hyperparameter is the most likely cause, and how should it be adjusted?

A) The batch size is too large and should be increased further
B) The number of hidden layers is too low and should be increased
C) The learning rate is too high and should be decreased
D) The activation function is too complex and should be removed entirely

---

**Q14.** In a deep neural network trained with sigmoid activations in every hidden layer, the weights in the earliest layers stop updating meaningfully even after many training epochs. What phenomenon does this describe?

A) Exploding gradients
B) Label leakage
C) Vanishing gradients
D) Data drift

---

**Q15.** A neural network engineer trains a deep classifier and observes 99% training accuracy but only 65% validation accuracy, with the gap widening over additional epochs. Which approach BEST addresses this issue?

A) Increase the learning rate to help the model converge faster
B) Remove the validation set so the model trains on more data
C) Add dropout layers and L2 regularization to reduce overfitting
D) Add more hidden layers to increase model capacity

---

**Q16.** A manufacturing company wants to build a system that inspects photos of circuit boards on an assembly line and flags defective units in real time. The spatial arrangement of components in the image is critical to detecting defects. Which neural network architecture is BEST suited for this task?

A) Convolutional Neural Network (CNN)
B) Recurrent Neural Network (RNN) with LSTM cells
C) A simple fully connected feedforward network
D) Autoregressive transformer decoder trained on text tokens

---

**Q17.** A financial services team needs a model to predict next-day stock closing prices using the past 60 days of sequential price data, where the order and temporal dependency between days matters. Which type of neural network should they select?

A) Convolutional Neural Network (CNN) with 2D convolutions
B) Recurrent Neural Network (RNN), such as an LSTM
C) A single-layer perceptron
D) Generative Adversarial Network (GAN)

---

**Q18.** In a Convolutional Neural Network architecture, what is the primary purpose of a pooling layer?

A) To reduce the spatial dimensions of feature maps while retaining the most important information
B) To apply a nonlinear activation function to increase model expressiveness
C) To convert the final feature maps into word embeddings for text generation
D) To randomly deactivate neurons during training to prevent overfitting

---

**Q19.** A legal research firm wants an AI assistant that can answer questions using regulatory documents that are updated every single day. The firm cannot afford to retrain or fine-tune the model daily. Which approach BEST meets this requirement?

A) Pretrain a new foundation model from scratch each week using the latest documents
B) Fine-tune the base model nightly on the newly published documents
C) Use Retrieval-Augmented Generation (RAG) to pull current documents into the prompt context at query time
D) Rely solely on the model's pretrained knowledge and prompt engineering alone

---

**Q20.** An LLM deployed in production has a context window of 4,096 tokens. A user's growing conversation history plus the new prompt totals 5,200 tokens. What is the expected behavior?

A) The model automatically expands its context window to fit the full input
B) The model compresses the entire input into a shorter summary without losing any information
C) The request processes normally with no effect on output quality
D) The oldest tokens are truncated or dropped so the input fits within the 4,096-token limit

---

**Q21.** A company wants its LLM to consistently use industry-specific jargon, a fixed tone, and a particular output format across all responses, independent of any external data source. Which technique is the BEST fit?

A) Retrieval-Augmented Generation to fetch style examples at query time
B) Increasing the context window size to include more tokens
C) Using a larger pretrained foundation model with no further customization
D) Fine-tuning the pretrained model on a curated dataset of examples in the desired jargon, tone, and format

---

**Q22.** In the transformer architecture, what does the self-attention mechanism fundamentally compute for each token in a sequence?

A) A weighted relevance score between that token's query vector and the key vectors of all other tokens, used to combine their value vectors
B) A fixed sliding window average over neighboring tokens
C) A sequential hidden state passed recurrently from the previous token
D) A convolutional filter applied uniformly across the entire input sequence

---

**Q23.** A legal firm wants its chatbot to answer questions using the firm's internal case documents, which are updated weekly. The chatbot must cite the exact source document and avoid fabricating legal precedents. Which approach BEST meets these requirements?

A) Fine-tune the LLM weekly on the updated case documents
B) Increase the LLM's temperature to improve creative legal reasoning
C) Use a larger pretrained LLM with no additional context
D) Retrieval-Augmented Generation (RAG) with the documents indexed in a vector store

---

**Q24.** An AI engineer builds a RAG system where document chunks are converted into vectors stored in a vector database. When a user submits a query, the system compares the query embedding to the stored embeddings to find relevant chunks. What property makes embeddings suitable for this comparison?

A) Embeddings store raw text as encrypted strings for secure retrieval
B) Embeddings compress text into fixed-length numeric vectors where semantic similarity corresponds to vector proximity
C) Embeddings are database indexes that sort documents alphabetically
D) Embeddings apply regex pattern matching to find exact keyword matches

---

**Q25.** A product team wants an LLM to solve multi-step arithmetic word problems reliably without additional training. Which prompting technique is MOST effective for improving reasoning accuracy on this task?

A) Chain-of-thought prompting that asks the model to reason step-by-step
B) Zero-shot prompting with no examples
C) Reducing the prompt to a single keyword
D) Increasing the model's temperature to 1.5

---

**Q26.** An engineer is configuring a text-to-image diffusion model and notices generated images don't closely follow the text prompt. Which parameter should be increased to make outputs adhere more closely to the prompt, at the risk of reduced image diversity?

A) Guidance scale (classifier-free guidance weight)
B) Batch size
C) Random seed value
D) Image resolution

---

**Q27.** A company builds a chatbot that must handle rare domain-specific words like 'cardiomyopathy' without treating them as unknown tokens. Which approach BEST handles this?

A) Word-level tokenization with a fixed vocabulary
B) Character-level one-hot encoding only
C) Byte-Pair Encoding (BPE) subword tokenization
D) Removing rare words during preprocessing

---

**Q28.** A legal-tech firm needs to extract person names, organizations, and dates from scanned contracts that have been converted to text. Which NLP task should they implement?

A) Sentiment Analysis
B) Named Entity Recognition (NER)
C) Text Summarization
D) Topic Modeling

---

**Q29.** A recommendation engine needs to find documents with similar meaning even when they use different wording (synonyms). Which text representation BEST supports this?

A) One-hot encoding
B) TF-IDF vectors
C) Dense word embeddings (e.g., Word2Vec, BERT embeddings)
D) Bag-of-words counts

---

**Q30.** When preparing text for a sentiment classifier that must correctly capture phrases like 'not good', which preprocessing configuration is MOST appropriate?

A) Remove all stopwords, including negations
B) Use unigrams only (n-gram range of 1,1)
C) Apply stemming only, with no n-gram changes
D) Use bigrams in addition to unigrams (n-gram range of 1,2) while retaining negation words

---

**Q31.** What is the key difference between stemming and lemmatization in text preprocessing?

A) Stemming requires a pretrained transformer model; lemmatization does not
B) Stemming crudely chops word endings using fixed rules; lemmatization uses vocabulary and morphological analysis to return valid dictionary (lemma) forms
C) Lemmatization is only used for numerical data
D) Stemming and lemmatization always produce identical output

---

**Q32.** A team has a small labeled dataset (500 examples) of support tickets they must classify into 5 categories with high accuracy, and they have limited time for training. Which approach BEST meets these requirements?

A) Train a Naive Bayes classifier with TF-IDF features
B) Build a custom transformer architecture from scratch
C) Use rule-based keyword matching
D) Fine-tune a pretrained transformer model (e.g., BERT) via transfer learning

---

**Q33.** A data science team is building a system that must distinguish the meaning of the word 'bank' when it appears in sentences like 'He sat on the river bank' versus 'She deposited money at the bank.' Static word embeddings trained with Word2Vec assign the same vector to 'bank' in both cases, causing downstream classification errors. Which approach BEST resolves this issue?

A) Increase the Word2Vec training corpus size to improve vector quality for ambiguous words
B) Replace the embeddings with TF-IDF vectors weighted by inverse document frequency
C) Use contextual embeddings generated by a pretrained transformer model, which produce a different vector for each occurrence of a word based on surrounding context
D) Encode each word as a one-hot vector to eliminate ambiguity in the representation

---

**Q34.** A developer needs to quickly classify the sentiment of customer reviews using a pretrained Hugging Face model, without writing any training code or manually loading a tokenizer. Which approach BEST meets this requirement?

A) Use the pipeline() function with task='sentiment-analysis'
B) Instantiate AutoModel.from_pretrained() and manually tokenize each review
C) Use the Trainer API with a custom TrainingArguments configuration
D) Fine-tune a BERT model from scratch on a labeled sentiment dataset

---

**Q35.** When loading a tokenizer for a specific pretrained checkpoint such as 'bert-base-uncased', which class automatically selects the correct tokenizer implementation matching that checkpoint's architecture?

A) TokenizerBase
B) AutoTokenizer
C) BertTokenizerFast only
D) PreTrainedModel

---

**Q36.** In the Hugging Face Trainer API, which TrainingArguments parameter controls how many full passes the model makes over the training dataset during fine-tuning?

A) learning_rate
B) per_device_train_batch_size
C) num_train_epochs
D) warmup_steps

---

**Q37.** A team has only 500 labeled examples and limited GPU budget, but needs a text classifier for a domain-specific task. Which approach BEST leverages transfer learning to achieve good performance under these constraints?

A) Train a transformer model from randomly initialized weights on the 500 examples
B) Manually label 50,000 additional examples before any training begins
C) Use only rule-based keyword matching instead of a model
D) Fine-tune a pretrained transformer model (e.g., DistilBERT) on the 500 labeled examples using the Trainer API

---

**Q38.** What is the primary role of a tokenizer in the Hugging Face transfer learning workflow?

A) Computing the final loss value during training
B) Selecting which pretrained model architecture to download
C) Converting raw text into numerical input IDs (and attention masks) that the model can process
D) Storing the trained model's final weights after fine-tuning

---

**Q39.** A developer wants to browse thousands of community-contributed and officially maintained pretrained models, filter by task (e.g., text-classification), and download a specific checkpoint by its repository ID. Which Hugging Face resource is designed for this?

A) The Datasets library documentation
B) The Hugging Face Model Hub
C) The Trainer API reference
D) The transformers library's internal cache directory

---

**Q40.** An engineer is fine-tuning a DistilBERT sequence classification model on a dataset of customer support tickets using the Hugging Face Trainer API. Ticket lengths vary from 5 to 400 tokens, and the engineer wants batches to be formed efficiently without errors from mismatched tensor shapes, while also preventing excessively long tickets from consuming unnecessary GPU memory. Which tokenizer call BEST meets these requirements?

A) tokenizer(texts, return_tensors='pt')
B) tokenizer(texts, padding='do_not_pad', truncation=False)
C) tokenizer(texts, padding=True, truncation=True, max_length=128)
D) tokenizer(texts, padding=True, truncation=False, max_length=512)

---

**Q41.** A team is building a GUI for an LLM-based chatbot. A key requirement is that tokens must appear incrementally in the chat window as the model generates them, rather than waiting for the full response. Which approach BEST meets this requirement?

A) Use a static HTML table to render the conversation history only after each full response is generated
B) Use Gradio's Interface with a function that returns a single complete string once generation finishes
C) Use Streamlit's st.write to display the full response only after the backend call returns
D) Use Gradio's ChatInterface (or Blocks) with a generator function that yields partial responses

---

**Q42.** A production Streamlit app performs image captioning with an inference call that takes 8-10 seconds. Users are abandoning the page because the UI appears frozen with no feedback. What is the BEST UX fix?

A) Increase the model's batch size so multiple images are processed in the background without informing the user
B) Remove the model loading step entirely from the app flow
C) Silently redirect users to a different page while the model runs
D) Wrap the inference call with st.spinner or a progress indicator so users see that processing is underway

---

**Q43.** A GUI needs to let a user upload an image and see the predicted class label along with its confidence score. Which Gradio output component is MOST appropriate for this purpose?

A) gr.Dataframe with image previews disabled
B) gr.Audio component
C) gr.Textbox containing only the raw class name string
D) gr.Label, which displays class names with their associated confidence scores

---

**Q44.** Which parameter of Gradio's launch() function controls whether a publicly shareable link is generated for demoing the app?

A) share=True
B) debug=True
C) server_name="0.0.0.0"
D) public=True

---

**Q45.** What is the key architectural difference between Gradio and Streamlit when building AI demo UIs?

A) Streamlit reruns the entire script top-to-bottom on every user interaction, while Gradio uses event-driven callbacks bound to specific components
B) Gradio only supports computer vision models while Streamlit only supports NLP models
C) Streamlit cannot be used with model inference code at all; only Gradio supports live inference
D) Gradio requires a dedicated database backend while Streamlit does not require any backend

---

**Q46.** A team has trained a fraud-detection model in a Jupyter notebook. They need to expose it so a web application can send transaction data and receive a real-time prediction, and the solution must be portable across development, staging, and production environments. Which approach BEST meets these requirements?

A) Export the notebook as a PDF and have developers manually re-implement the prediction logic in each environment's codebase
B) Wrap the model in a REST API using a framework like FastAPI, package the API and its dependencies into a Docker container, and deploy that container to each environment
C) Share the trained model file over email and have each environment load it directly into a local Python script run manually
D) Embed the model weights directly into the frontend JavaScript code so predictions happen in the browser

---

**Q47.** A deployed classification model's prediction accuracy has started degrading over several months even though no code changes were made. Which monitoring practice would have detected the root cause earliest?

A) Tracking only the API's HTTP response time and uptime percentage
B) Monitoring CPU and memory utilization of the container running the model
C) Monitoring for data drift by comparing the statistical distribution of incoming production data against the training data distribution
D) Tracking the number of API calls made per day to the model endpoint

---

**Q48.** A data science team needs to present a newly deployed credit-risk model's behavior to non-technical business stakeholders who will decide whether to approve its use. Which approach is MOST appropriate for this communication?

A) Send stakeholders the raw Python training script and ask them to review the code
B) Give stakeholders direct read access to the production database tables used for training
C) Share only the final accuracy percentage with no additional context or explanation
D) Provide a model card summarizing the model's purpose, performance metrics, limitations, and intended use cases in plain language with visual explanations

---

