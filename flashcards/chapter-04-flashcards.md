## Chapter 4: CNNs, RNNs, and Real-World Neural Network Applications — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Purpose of a convolutional filter in a CNN? | Detects local spatial patterns (edges, textures, shapes) via a small learned weight matrix slid across the input. Exam tip: filter size and stride control the output feature map's dimensions. |
| 2 | Purpose of a pooling layer (e.g., max pooling)? | Reduces spatial dimensions of feature maps, lowers compute/parameters, and adds robustness to small translations in the image. Exam tip: pooling does not learn weights. |
| 3 | CNN feature-extraction hierarchy order (shallow to deep)? | Early layers detect edges/textures → middle layers detect parts/patterns → deep layers detect whole objects/high-level concepts. Exam tests this progression. |
| 4 | Why do vanilla RNNs struggle with long sequences? | Gradients are repeatedly multiplied during backpropagation through time (BPTT), causing them to vanish (or explode) exponentially, preventing learning of long-range dependencies. |
| 5 | LSTM gate structure? | Three gates: input, forget, output — control what information enters, is retained in, and leaves the cell state. The forget gate is key to mitigating vanishing gradients. |
| 6 | GRU vs LSTM? | GRU uses 2 gates (reset, update) vs LSTM's 3 gates; GRU has fewer parameters and trains faster, with comparable performance on many tasks. Exam tip: choose GRU when compute/data is limited. |
| 7 | CNN vs RNN vs Transformer — best for static image data? | CNN — convolution + pooling exploit spatial locality and translation invariance, the standard choice for image classification/detection. |
| 8 | CNN vs RNN vs Transformer — best for long-range dependencies in long sequences (e.g., long text)? | Transformer — self-attention relates any two positions directly in one layer, avoiding the vanishing-gradient limits of RNNs on long sequences. |
| 9 | CNN vs RNN — best for short sequential data with limited compute/data? | RNN/LSTM/GRU — far fewer parameters than transformers, well suited to small, short sequential datasets like brief time series. |
| 10 | Object detection vs image classification — key architectural difference? | Object detection adds a bounding-box regression (localization) head alongside the classification head on a CNN backbone; classification outputs only a single label. |
| 11 | Effect of a 2x2 max pooling layer with stride 2 on a feature map? | Halves both spatial dimensions (e.g., 4x4 → 2x2) by taking the max value in each non-overlapping 2x2 region. Common convention in CNN architectures. |
| 12 | Classic architecture family for streaming speech recognition (frame-by-frame audio)? | RNN/LSTM/GRU — maintain hidden state across time steps, suited to sequential audio processing; many modern systems (e.g., Whisper) now use transformer-based encoders instead. |
