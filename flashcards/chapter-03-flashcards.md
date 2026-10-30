## Chapter 3: Neural Networks: Perceptrons to Backpropagation — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Sigmoid activation output range and primary use case | (0, 1). Used for binary classification output or independent multi-label outputs. Exam tip: causes vanishing gradients in deep hidden layers — avoid stacking many sigmoid hidden layers. |
| 2 | Softmax vs Sigmoid for output layer — when to use which? | Softmax: single-label, mutually exclusive multi-class (outputs sum to 1). Sigmoid: binary classification or multi-label where classes are independent (each output 0-1 independently). |
| 3 | Why is ReLU preferred over sigmoid/tanh in deep hidden layers? | ReLU gradient is constant (1) for positive inputs, avoiding vanishing gradients. Sigmoid/tanh saturate near 0 or ±1, causing gradients to shrink toward zero across many layers. |
| 4 | Cross-entropy loss vs Mean Squared Error — when to use which? | Cross-entropy: classification tasks (binary or categorical), measures distance between predicted and true probability distributions. MSE: regression tasks with continuous targets. |
| 5 | Symptom: training loss low, validation loss high and rising after some epoch | Overfitting. Fix with dropout, L2 regularization, early stopping, or more training data. Exam tip: the divergence point is where early stopping should trigger. |
| 6 | Symptom: both training and validation loss are high and plateaued | Underfitting. Fix by increasing model capacity (more layers/units), training longer, or improving features — NOT by adding regularization (that worsens underfitting). |
| 7 | Learning rate too high vs too low — training symptoms | Too high: loss oscillates or diverges (NaN possible). Too low: loss decreases very slowly, may appear stuck. Exam tip: NaN loss is almost always a learning-rate-too-high clue. |
| 8 | What does Adam optimizer combine that gives it an advantage over plain SGD? | Momentum (first moment estimate) + per-parameter adaptive learning rates (second moment estimate, like RMSProp). Converges faster with less manual LR tuning than vanilla SGD. |
| 9 | Dropout regularization — how does it work? | Randomly zeroes out a fraction of neuron activations during each training step (e.g., rate 0.2–0.5), forcing the network to not rely on any single neuron, reducing overfitting. Disabled at inference time. |
| 10 | L2 regularization effect on weights | Adds a penalty term (lambda × sum of squared weights) to the loss, discouraging large weight values and producing smoother, less overfit decision boundaries. Also called weight decay. |
| 11 | Epoch vs batch vs iteration — definitions | Epoch: one full pass through the entire training dataset. Batch: subset of data processed before one weight update. Iteration: one weight update (one batch processed). Total iterations per epoch = dataset size / batch size. |
| 12 | Perceptron output formula | output = activation(sum(weight_i × input_i) + bias). The bias allows shifting the activation threshold independent of inputs. Exam tip: without bias, the decision boundary is forced through the origin. |
