# Attention

---

## 1. Introduction
- A sequence-to-sequence model is a model that takes a sequence of items (words, letters, features of an image, etc.) and outputs another sequence of items.
- Attention allows the model to focus on the relevant parts of the input sequence as needed.

---

## 2. Core Idea
- First, the encoder passes a lot more data to the decoder. Instead of passing **only the last hidden state of the encoding stage**, the encoder passes **all the hidden states** to the decoder.
- An attention decoder does an extra step before producing its output. In order to focus on the parts of the input that are relevant to this decoding time step, the decoder does the following:
    1. Look at the set of encoder hidden states it received – each encoder hidden state is most associated with a certain word in the input sentence.
    2. Give each hidden state a score (let’s ignore how the scoring is done for now).
    3. Multiply each hidden state by its softmaxed score, thus amplifying hidden states with high scores, and drowning out hidden states with low scores.

- **Analogy**: Just like how humans pay attention to important words when reading a sentence, the attention mechanism helps the model focus on important parts of the input sequence.

- The attention decoder RNN takes in the embedding of the `<END>` token and an initial decoder hidden state.
- The RNN processes its inputs, producing an output and a new hidden state vector (**h₄**). The output is discarded.
- **Attention Step**: We use the encoder hidden states and the **h₄** vector to calculate a context vector (**C₄**) for this time step.
- We concatenate **h₄** and **C₄** into one vector.
- We pass this vector through a feedforward neural network (trained jointly with the model).
- The output of the feedforward neural network indicates the output word for this time step.
- Repeat the process for the next time steps.

**Source**- https://jalammar.github.io/visualizing-neural-machine-translation-mechanics-of-seq2seq-models-with-attention/