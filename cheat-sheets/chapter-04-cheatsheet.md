## Chapter 4 Cheat Sheet: CNNs, RNNs, and Applications

### Architecture Selection by Data Type
| Data Type | Best Architecture | Why |
|---|---|---|
| Static images | CNN | Exploits spatial locality + translation invariance via convolution/pooling |
| Short sequences, limited compute/data | RNN / LSTM / GRU | Fewer params than transformers, handles short-to-moderate sequences |
| Long sequences, long-range dependencies | Transformer | Self-attention relates distant tokens directly, no vanishing-gradient decay |
| Audio/speech (streaming) | LSTM/GRU (classic) or Transformer encoder (modern, e.g. Whisper) | Sequential memory or attention over time frames |
| Time series forecasting | RNN/LSTM/GRU (or Transformer for very long horizons) | Captures temporal order and trends |

### CNN Core Components
- **Convolutional filter**: small learned matrix (commonly 3x3 or 5x5) slid across input to detect local patterns (edges → textures → object parts → objects).
- **Pooling (max/average)**: downsamples feature maps, reduces compute, adds translation invariance. Common: 2x2 window, stride 2 → halves spatial dims.
- **Feature hierarchy**: shallow layers = low-level features; deep layers = high-level/abstract features.
- **Object detection** = CNN backbone + classification head + bounding-box regression head (unlike plain classification, which has only the classification head).

### RNN Core Problem: Vanishing Gradients
- Backpropagation Through Time (BPTT) repeatedly multiplies gradients by the same weight matrix at each time step.
- Over long sequences, gradients shrink toward zero (vanish) or grow unbounded (explode), preventing the network from learning long-range dependencies.

### LSTM / GRU Fixes
| Feature | LSTM | GRU |
|---|---|---|
| Gates | Input, Forget, Output (3) | Reset, Update (2) |
| Parameters | More | Fewer |
| Training speed | Slower | Faster |
| Use case | Longer/complex sequences, more data | Shorter sequences, limited data/compute |

Both use gating mechanisms that allow gradients to flow through the cell state largely unchanged, directly addressing vanilla RNN vanishing gradients.

### Exam Decision Rules
1. **Spatial, grid-like data (images)** → CNN.
2. **Sequential data, short/limited data** → RNN/LSTM/GRU.
3. **Sequential data, long-range dependencies, ample data/compute** → Transformer.
4. **Need both localization and classification** → CNN backbone + detection heads (not plain classification CNN).
5. **"Vanishing gradient" + "long sequence" in question stem** → answer involves LSTM/GRU gating or Transformer attention, never vanilla RNN.

### Common Exam Traps
- Choosing a vanilla RNN for long-sequence tasks (ignores vanishing gradient).
- Confusing pooling (no learned weights, downsampling) with convolution (learned weights, feature detection).
- Assuming transformers are only for text — modern vision (ViT) and audio (Whisper) also use transformers, but CNN/RNN heuristics still apply to classic exam scenarios.
- Picking plain image classification architecture for an object detection scenario (missing the localization head).
