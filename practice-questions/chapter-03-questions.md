## Chapter 3: Neural Networks: Perceptrons to Backpropagation — Practice Questions

**Q1.** A model trained for binary classification achieves 99% training accuracy but only 62% validation accuracy. The training loss steadily decreases while validation loss starts increasing after epoch 15. Which combination of actions is the BEST response?

A) Increase the learning rate and train for more epochs to escape the local minimum
B) Add dropout layers and L2 weight regularization, and stop training around epoch 15 using early stopping
C) Switch the loss function from binary cross-entropy to mean squared error
D) Remove the validation set and train on 100% of the data to give the model more examples

<details>
<summary>Answer</summary>

**Correct: B**

Diverging train/validation loss after a point is the textbook overfitting signature. Dropout, L2 regularization, and early stopping at the divergence point directly address overfitting.

**Why the others are wrong:**
- Higher learning rate and more epochs would worsen overfitting, not fix it
- MSE is the wrong loss for binary classification regardless of overfitting; it doesn't address the core problem
- Removing the validation set eliminates your ability to detect overfitting at all

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** You are designing the output layer for a model that classifies an image into exactly one of 10 mutually exclusive categories. Which activation function should the output layer use?

A) Sigmoid
B) Softmax
C) ReLU
D) Tanh

<details>
<summary>Answer</summary>

**Correct: B**

Softmax converts logits into a probability distribution across mutually exclusive classes that sums to 1, which is required for single-label multi-class classification.

**Why the others are wrong:**
- Sigmoid is for binary or multi-label (independent) classification, not mutually exclusive multi-class
- ReLU is used in hidden layers for non-linearity, not as a probability output; it is unbounded and can't represent a distribution
- Tanh outputs values between -1 and 1 and is not normalized into a probability distribution

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** During training, the loss decreases for a few epochs, then oscillates wildly and occasionally increases to very large values (NaN in some batches). What is the MOST likely cause?

A) The batch size is too large
B) The model does not have enough layers
C) The learning rate is too high
D) Dropout rate is set too low

<details>
<summary>Answer</summary>

**Correct: C**

A learning rate that is too high causes gradient updates to overshoot the minimum, producing oscillation, divergence, and exploding values (NaN).

**Why the others are wrong:**
- Large batch size typically produces smoother, more stable gradients, not instability
- Insufficient layers would cause underfitting with a flat high loss, not oscillation/divergence
- Low dropout affects overfitting risk, not numerical instability during training

</details>

---

**Q4.** Which hidden-layer activation function is the standard default choice for deep feedforward networks because it mitigates the vanishing gradient problem compared to sigmoid and tanh?

A) Sigmoid
B) ReLU
C) Softmax
D) Linear (identity)

<details>
<summary>Answer</summary>

**Correct: B**

ReLU outputs the input directly for positive values with a constant gradient of 1, avoiding the saturation that causes vanishing gradients in sigmoid/tanh across deep networks.

**Why the others are wrong:**
- Sigmoid saturates at both ends, producing near-zero gradients in deep networks — this is the vanishing gradient problem
- Softmax is reserved for multi-class output layers, not hidden layers
- A linear activation collapses the network to a single linear transformation regardless of depth, removing non-linearity entirely

</details>

---

**Q5.** A regression model predicting house prices needs a loss function. Which should be used?

A) Mean squared error
B) Categorical cross-entropy
C) Binary cross-entropy
D) Softmax loss

<details>
<summary>Answer</summary>

**Correct: A**

MSE penalizes the squared difference between predicted and actual continuous values, which is the standard loss for regression tasks.

**Why the others are wrong:**
- Categorical cross-entropy requires a probability distribution over discrete classes, not applicable to continuous output
- Binary cross-entropy is for two-class classification probabilities, not continuous values
- 'Softmax loss' is not a standalone loss function — softmax is an activation typically paired with cross-entropy, not MSE-style regression

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** A team wants faster convergence than plain stochastic gradient descent, with per-parameter adaptive learning rates and momentum, without extensive manual learning-rate tuning. Which optimizer BEST fits this requirement?

A) Adam
B) Plain SGD with a fixed learning rate
C) Gradient descent with a manually decayed learning rate schedule only
D) Batch gradient descent using the entire dataset per step

<details>
<summary>Answer</summary>

**Correct: A**

Adam combines momentum (first moment) and adaptive per-parameter learning rates (second moment estimates), converging faster than plain SGD with less manual tuning — it is the default choice for most deep learning tasks.

**Why the others are wrong:**
- Plain SGD has no adaptive learning rate and converges slower, often needing careful tuning
- Manual decay schedules require ongoing tuning effort, the opposite of what's requested
- Full-batch gradient descent is computationally expensive and doesn't address the adaptive-rate requirement

</details>

---

**Q7.** A network's training loss and validation loss are both high and plateau early, with training accuracy far below expected performance even after many epochs. What does this indicate?

A) Underfitting — the model may need more capacity, more features, or more training time
B) Overfitting — add dropout immediately
C) The learning rate is too low to cause any effect
D) The validation set is too small to be meaningful

<details>
<summary>Answer</summary>

**Correct: A**

Both train and validation loss being high and plateaued indicates the model isn't fitting the data well — a classic underfitting signature, often fixed by increasing model capacity or training duration.

**Why the others are wrong:**
- Overfitting shows a gap where training loss is low and validation loss is high, not both high
- A too-low learning rate would also show flat/slow loss decrease but the root issue described (poor fit) is model capacity, not just LR — and this isn't the standard exam-tested diagnostic pairing for this symptom
- Validation set size is a secondary concern, not the primary explanation for consistently high loss on both sets

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** Which statement correctly differentiates the forward pass from backpropagation in a neural network?

A) The forward pass computes gradients; backpropagation computes the output predictions
B) The forward pass computes predictions from inputs using current weights; backpropagation computes gradients of the loss with respect to weights by propagating error backward
C) Forward pass and backpropagation are two names for the same operation
D) Backpropagation only runs during inference, not training

<details>
<summary>Answer</summary>

**Correct: B**

The forward pass flows data through the network to produce an output; backpropagation then applies the chain rule to compute gradients of the loss with respect to each weight, which are used to update weights.

**Why the others are wrong:**
- This reverses the actual roles of each step
- They are distinct steps occurring in a specific order every training iteration
- Backpropagation only occurs during training to compute gradients; inference uses only the forward pass

</details>

---

