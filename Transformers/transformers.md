# Transformers

---

## 1. Introduction
- **Transformer** – a model that uses attention to boost the speed with which these models can be trained.
- The biggest benefit, however, comes from how the Transformer lends itself to **parallelization**. It is in fact Google Cloud’s recommendation to use the Transformer as a reference model for their Cloud TPU offering.
- Transformer architecture uses **self-attention** to transform one whole sentence into a single sentence. This is useful where older models work step by step and helps overcome challenges seen in models like RNNs and LSTMs.
    - Traditional models like **RNNs (Recurrent Neural Networks)** suffer from the **vanishing gradient problem**, leading to long-term memory loss.
    - RNNs process text sequentially, analyzing words one at a time.
- Traditional models struggle with context dependence, whereas the Transformer model, through its self-attention mechanism, processes the entire sentence in parallel, addressing these issues and making it significantly more effective at understanding context.

---

## 2. Core Components

### 2.1 Self-Attention Mechanism
- Allows transformers to determine which words in a sentence are most relevant to each other.
- Uses a **scaled dot-product attention** approach.
- Each word in a sequence is mapped to three vectors:
    - **Query (Q)**
    - **Key (K)**
    - **Value (V)**
- Attention scores are computed as:
  
Attention(Q, K, V) = softmax((Q Kᵀ) / √d_k) V


- These scores determine how much attention each word should pay to others.

---

### 2.2 Positional Encoding
- Unlike RNNs, transformers lack an inherent understanding of word order because they process data in parallel.
- **Positional Encodings** are added to token embeddings, providing information about the position of each token within a sequence.

---

### 2.3 Multi-Head Attention
- Instead of a single attention mechanism, transformers use **multiple attention heads** running in parallel.
- Each head captures different relationships or patterns in the data, enriching the model’s understanding.

---

### 2.4 Position-wise Feed-Forward Networks
- Consists of two linear transformations with a **ReLU activation**.
- Applied independently to each position in the sequence.

Mathematically:

FFN(x) = max(0, xW₁ + b₁) W₂ + b₂


- This helps refine the encoded representation at each position.

---

## 3. Encoder-Decoder Architecture
- The encoder-decoder structure is key to transformer models.
  - The **encoder** processes the input sequence into a vector.
  - The **decoder** converts this vector back into a sequence.

- Each encoder and decoder layer includes:
  - **Self-Attention Layer**
  - **Feed-Forward Layer**

- In the decoder, an **encoder-decoder attention layer** is added to focus on relevant parts of the input.

### Encoder Structure
- Typically consists of **6 layers**.
- Each layer has:
  - Self-Attention Mechanism
  - Feed-Forward Neural Network

### Decoder Structure
- Also consists of **6 layers**, but with an additional **encoder-decoder attention mechanism**.
- This allows the decoder to focus on relevant parts of the input sentence while generating output.

---

## 4. Applications of Transformers
- **NLP Tasks**: Machine translation, text summarization, named entity recognition, sentiment analysis.
- **Speech Recognition**: Converting audio signals into transcribed text.
- **Computer Vision**: Image classification, object detection, image generation.
- **Recommendation Systems**: Personalized recommendations based on user preferences.
- **Text and Music Generation**: Generating articles, composing music.

---

## 5. Conclusion
Transformers have redefined deep learning across NLP, computer vision, and beyond. With advancements like **BERT**, **GPT**, and **Vision Transformers (ViTs)**, they continue to push the boundaries of AI, language understanding, and multimodal learning.

---

### Source
[Getting Started with Transformers – GeeksforGeeks](https://www.geeksforgeeks.org/machine-learning/getting-started-with-transformers/)
