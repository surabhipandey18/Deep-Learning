# Recurrent Neural Networks (RNN) — Intuitive Overview and PyTorch Implementation

##  Intuitive Overview

- **Main Use Case:** RNNs are ideal for sequential data. While CNNs operate on fixed-size inputs/outputs with a fixed number of computation steps, RNNs process sequences of arbitrary length by operating over sequences of vectors.
- **Optimization Analogy:** Training vanilla neural networks = optimization over functions.  
  Training recurrent nets = optimization over programs.
- **Sequential Modeling Power:** Even non-sequential data can be formulated and processed sequentially by RNNs.

---

## Key Architecture Points

- **Components:** Input, Hidden State, Weights/Parameters, Output
- **Multi-layer Perceptron comparison:** Each hidden layer traditionally has independent weights/biases; order/structure is lost when layers don’t interact.
- **Parameter Sharing:** RNNs share parameters/weights across time steps, allowing the network to retain context over variable-length sequences.
- **Output:** Often, the final hidden state is used for prediction via a dense output layer (e.g., with a softmax for classification).
- **Loss Calculation:** Cross-entropy loss is typically used for classification.
    - \[
      L_θ(y, y'_t) = -y_t \log y'_t 
      \]
    - Where \( θ = \{W_h, W_x, W_y\} \)
- **Backpropagation Through Time (BPTT):**
    - The network is “unfolded” across time steps, and gradients are computed through all steps.
    - Loss is backpropagated through both hidden/recurrent and dense layers.

---

-**Loss Calculated**:
<img width="800" height="435" alt="image" src="https://github.com/user-attachments/assets/d35efc1f-5da5-4470-b423-7c8e4a813f06" />


##  When to Use

- When data has meaningful order (sequences, time series, language, etc.)
- Even for non-sequence data, can sometimes be reformulated to take advantage of sequential processing.
- Allows modeling of context and dependencies over arbitrary-length input.

> [Recurrent neural networks](https://towardsdatascience.com/recurrent-neural-networks-d4642c9bc7ce) model sequential data by keeping a context vector across time \( t \).

---

## Strengths

- Preserves sequence order.
- Can map:
    - Variable-length input sequence → fixed-size vector
    - Fixed-size input → variable-length sequence
    - Sequence-to-sequence mapping
- Fully differentiable (trainable by gradient descent)

---

##  Weaknesses / Challenges

**Vanishing Gradient:**  
- Example: If weight \( w=0.5 \) and network depth is 50, the input is multiplied by \( 0.5^{50} \). Gradients during backprop become tiny, stalling learning for long-term dependencies.

**Exploding Gradient:**  
- Example: If weight \( w=2 \), network depth is 50, the input is multiplied by \( 2^{50} \), which explodes in size and can make weights NaN.

These make it hard for vanilla RNNs to learn very long-range dependencies in practice. Common solutions include gradient clipping, LSTM/GRU architectures.

---

##  PyTorch Implementation Notes

- **Forward Pass:** Main parameters: \( W_{hh} \), \( W_{xh} \), \( W_{hy} \)
- **Hidden State:** Initialized as zero vector.
- **Activation:** `torch.tanh` is typically used for squashing activations to [-1, 1].
- **Update Rule:**  
    \[
    h_t = \tanh(W_{hh} h_{t-1} + W_{xh} x_t)
    \]
- **Parameter Training:** Find matrices that map sequences to desired outputs (e.g., via cross-entropy loss).
- **Going Deep:** Improved performance often observed with stacking RNN layers (deep RNNs).

---

## References & Further Reading

- [Neptune AI: Recurrent Neural Network Guide](https://neptune.ai/blog/recurrent-neural-network-guide)
- [Andrej Karpathy: The Unreasonable Effectiveness of Recurrent Neural Networks](https://karpathy.github.io/2015/05/21/rnn-effectiveness/)
- [Towards Data Science: RNNs](https://towardsdatascience.com/recurrent-neural-networks-d4642c9bc7ce)

---
