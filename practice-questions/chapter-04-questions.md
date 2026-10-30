## Chapter 4: CNNs, RNNs, and Real-World Neural Network Applications — Practice Questions

**Q1.** A factory wants to automatically flag defective parts from photos taken on an assembly line camera. Which architecture BEST meets this requirement?

A) A vanilla RNN processing each pixel row sequentially
B) A fully connected network with no convolution or pooling
C) An LSTM trained on flattened pixel vectors
D) A CNN with convolutional and pooling layers followed by a classification head

<details>
<summary>Answer</summary>

**Correct: D**

CNNs exploit spatial locality and translation invariance in image data through convolutional filters and pooling, making them the standard choice for image classification tasks.

**Why the others are wrong:**
- RNNs are designed for sequential/temporal data, not 2D spatial image data, and processing pixels row-by-row discards spatial structure.
- Fully connected networks ignore spatial locality, require far more parameters, and don't generalize well to shifted/rotated images.
- LSTMs add sequential memory, which is irrelevant for a single static image and flattening destroys 2D spatial relationships.

</details>

---

**Q2.** A team is building a model to classify the sentiment of full customer support transcripts where relevant context can appear hundreds of tokens apart. Which architecture BEST handles this?

A) A transformer using self-attention
B) A vanilla RNN with a single hidden layer
C) A CNN with 3x3 filters
D) An LSTM with a very short sequence length cap

<details>
<summary>Answer</summary>

**Correct: A**

Self-attention lets a transformer directly relate any two tokens regardless of distance in one layer, making it the best fit for long-range dependencies in long text.

**Why the others are wrong:**
- Vanilla RNNs suffer from vanishing gradients, losing information from tokens far back in the sequence.
- CNNs with small fixed filters capture only local n-gram style patterns, not long-range dependencies.
- Capping sequence length on an LSTM would discard the distant context the task actually needs.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A startup has a small dataset of short (20-timestep) sensor readings and limited GPU budget, and needs to forecast the next value. Which architecture BEST fits these constraints?

A) A full transformer with multi-head self-attention
B) A deep CNN with 50+ convolutional layers
C) A vanilla RNN with no gating mechanism
D) A GRU-based recurrent network

<details>
<summary>Answer</summary>

**Correct: D**

GRUs have fewer parameters than LSTMs/transformers, train efficiently on small datasets, and handle short sequences well while mitigating vanishing gradients via gating.

**Why the others are wrong:**
- A full transformer is typically overkill and data-hungry for a 20-step sequence with limited compute.
- A deep CNN is not naturally suited to short sequential forecasting and adds unnecessary depth/compute.
- A vanilla RNN still suffers from vanishing gradients, even over moderately short sequences, hurting forecast accuracy.

</details>

---

**Q4.** Which combination of components is used in a typical object detection pipeline but NOT in a basic image classification pipeline?

A) Convolutional filters only
B) Pooling layers only
C) A bounding-box regression head alongside the classification head
D) A softmax output layer

<details>
<summary>Answer</summary>

**Correct: C**

Object detection extends a CNN backbone with a localization (bounding-box regression) head in addition to classification, so the model outputs both 'what' and 'where'.

**Why the others are wrong:**
- Convolutional filters are used in both classification and detection backbones.
- Pooling layers also appear in both classification and detection architectures.
- Softmax output layers are common to classification tasks as well, not unique to detection.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** For streaming speech recognition where audio must be processed frame-by-frame in real time with memory of prior frames, which architecture family is classically BEST suited?

A) A feedforward network with no memory
B) A CNN with only 1x1 filters
C) An LSTM or GRU based recurrent network
D) A decision tree ensemble

<details>
<summary>Answer</summary>

**Correct: C**

LSTM/GRU architectures maintain hidden state across time steps, making them well suited to sequential audio frames where order and memory of prior context matter.

**Why the others are wrong:**
- A feedforward network has no mechanism to retain information across time steps, losing sequential context.
- 1x1 convolutional filters only mix channel information at a single point and don't model temporal sequence memory.
- Decision tree ensembles don't model sequential dependencies and aren't a neural architecture for this task.

</details>

---

**Q6.** What is the primary purpose of a pooling layer in a CNN?

A) To increase the number of color channels in the feature map
B) To replace the need for an activation function
C) To reduce spatial dimensions while retaining the most salient features and adding translation invariance
D) To convert the feature map into a probability distribution

<details>
<summary>Answer</summary>

**Correct: C**

Pooling (e.g., max pooling) downsamples feature maps, reducing computation and parameters while making the representation more robust to small spatial shifts.

**Why the others are wrong:**
- Pooling does not add channels; that is the role of convolutional filters with multiple output channels.
- Pooling is a separate operation from activation functions and doesn't replace them.
- Converting to a probability distribution is the role of a softmax layer, not pooling.

</details>

---

**Q7.** Which mechanism specifically allows an LSTM to mitigate the vanishing gradient problem that affects vanilla RNNs?

A) Gated cell state with forget/input/output gates controlling information flow
B) A larger learning rate applied uniformly across all weights
C) Replacing backpropagation with forward-only inference
D) Using only ReLU activations instead of sigmoid/tanh

<details>
<summary>Answer</summary>

**Correct: A**

The LSTM's gated cell state allows gradients to flow through time largely unchanged when the forget gate is open, directly addressing the vanishing gradient issue of vanilla RNNs.

**Why the others are wrong:**
- Changing the learning rate doesn't address the structural cause of vanishing gradients across many time steps.
- LSTMs still use backpropagation through time; forward-only inference wouldn't allow training at all.
- Activation choice alone does not solve vanishing gradients over long sequences; the gating structure is the key fix.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** Why do vanilla RNNs struggle to learn dependencies across long sequences?

A) Repeated multiplication of gradients during backpropagation through time causes them to shrink or explode exponentially
B) They have too many parameters, causing overfitting on short sequences
C) They cannot process sequences of variable length
D) They require labeled data for every single time step

<details>
<summary>Answer</summary>

**Correct: A**

During backpropagation through time, gradients are repeatedly multiplied by the same weight matrix at each time step, causing them to vanish (or explode) exponentially over long sequences, which prevents learning long-range dependencies.

**Why the others are wrong:**
- Vanilla RNNs actually have relatively few parameters compared to transformers; overfitting isn't the core long-sequence issue.
- RNNs can process variable-length sequences by design; this isn't their limitation.
- RNNs can be trained with labels only at the final time step (e.g., sequence classification); per-step labels aren't required.

</details>

---

