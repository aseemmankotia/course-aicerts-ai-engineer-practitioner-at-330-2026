## Chapter 3 Cheat Sheet: Perceptrons to Backpropagation

### Perceptron Structure
`output = activation(Σ(w_i · x_i) + b)`
- Weights: learned importance of each input
- Bias: shifts decision boundary (without it, boundary passes through origin)

### Activation Function Selection
| Function | Range | Best Use | Exam Trap |
|---|---|---|---|
| Sigmoid | (0,1) | Binary output, multi-label output | Vanishing gradients if used in deep hidden layers |
| Tanh | (-1,1) | Hidden layers (zero-centered) | Still saturates at extremes |
| ReLU | [0,∞) | Default hidden layer choice | "Dying ReLU" — neurons stuck at 0 |
| Softmax | (0,1), sums to 1 | Multi-class single-label output | Never use for multi-label or regression |

### Loss Function Selection
| Task | Loss |
|---|---|
| Regression | Mean Squared Error (MSE) |
| Binary classification | Binary Cross-Entropy |
| Multi-class single-label | Categorical Cross-Entropy (paired with Softmax) |

### Forward Pass vs Backpropagation
- **Forward pass**: inputs → weights/activations → prediction
- **Backpropagation**: chain rule computes ∂Loss/∂weight, propagated output → input, used to update weights via optimizer

### Optimizers
| Optimizer | Key Trait |
|---|---|
| SGD | Simple, needs manual LR tuning, can be slow |
| SGD + Momentum | Smooths updates, accelerates convergence |
| Adam | Adaptive per-parameter LR + momentum; common default |

### Learning Rate Effects
- **Too high** → oscillating/diverging loss, possible NaN
- **Too low** → very slow convergence, loss appears flat
- **Just right** → smooth, steadily decreasing loss curve

### Overfitting vs Underfitting (Loss Curve Diagnosis)
| Symptom | Diagnosis | Fix |
|---|---|---|
| Train loss low, val loss high & rising | Overfitting | Dropout, L2 regularization, early stopping, more data |
| Train & val loss both high, plateaued | Underfitting | More capacity, train longer, better features |
| Train & val loss both low and close | Good fit | — |

### Regularization Techniques
- **Dropout**: randomly zero activations during training (rate ~0.2–0.5); off at inference
- **L2 (weight decay)**: penalizes large weights, adds λ·Σw² to loss
- **Early stopping**: halt training at the epoch where val loss starts rising

### Training Dynamics Definitions
- **Epoch**: one full pass over training data
- **Batch size**: samples per weight update
- **Iteration**: one weight update (dataset size / batch size = iterations per epoch)
- Smaller batches → noisier but sometimes better-generalizing updates; larger batches → smoother, more stable gradients but more memory

### Quick Exam Rules
- Multi-class single-label → Softmax + Categorical Cross-Entropy
- Binary → Sigmoid + Binary Cross-Entropy
- Regression → Linear output + MSE
- Diverging/NaN loss → learning rate too high
- Gap between train/val loss growing → overfitting → regularize or stop early
