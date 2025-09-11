# Today’s Learning Summary

## Topics Covered:
- Regularization
- Batch Normalization
- AdamW Optimizer

---

## 1. Regularization

Regularization is used to control the capacity of neural networks and prevent overfitting.

### Types of Regularization:

#### L2 Regularization (Ridge)
- Most common type.
- Penalizes the squared magnitude of all parameters directly in the loss function.
- For every weight $w$, we add the term:
  
  $\frac{1}{2} \lambda w^2$

  
  where $\lambda$ is the regularization strength.
  
- Encourages diffuse weight vectors and penalizes large, peaky weights.
- Gradient descent update becomes:
  
   $w \mathrel{+}= -\lambda \cdot w$

  → The weight decays linearly towards zero.

---

#### Weight Decay
- Similar to L2 regularization.
- Applied directly in the optimization step rather than the loss function.
- Mathematically, the update rule is:
  
  $w = (1 - \lambda) \cdot w - \alpha \cdot \text{gradient}$
  
- Effectively achieves the same as L2 regularization.

---

#### L1 Regularization (Lasso)
- Adds the term:
  
  $\lambda |w|$
  
- Encourages sparsity in the weight vector → Many weights become exactly zero.
- Useful for feature selection.
- Can be combined with L2 as Elastic Net Regularization:
  
  $\lambda_1 |w| + \frac{1}{2} \lambda_2 w^2$
  
- Empirically, if feature selection isn’t the goal, L2 often performs better.

---

#### Dropout
- Simple yet extremely effective.
- Randomly keeps a neuron active with probability $p$ (a hyperparameter) or sets it to 0 during training.
- Helps prevent co-adaptation of neurons.
- Behaves differently in training and testing phases (scales appropriately during testing).

---

## 2. Batch Normalization (BatchNorm)

Batch Normalization accelerates convergence of deep networks by improving:
- Preprocessing
- Numerical stability
- Regularization

It is applied to individual layers (optionally to all layers).

### How BatchNorm Works (Mathematical Expression):

For a minibatch $B$, and input $x \in B$, the batch normalization is computed as:

$$
\mu_B = \frac{1}{|B|} \sum_{x \in B} x
$$

$$
\sigma_B^2 = \frac{1}{|B|} \sum_{x \in B} (x - \mu_B)^2
$$

$$
\text{BN}(x) = \gamma \cdot \frac{x - \mu_B}{\sqrt{\sigma_B^2 + \epsilon}} + \beta
$$

- $\gamma$ and $\beta$ are learnable scale and shift parameters.
- $\epsilon > 0$ is added for numerical stability (prevents division by zero).

---

### Important Notes:
- Don’t apply BatchNorm with minibatches of size 1 → insufficient data to estimate reliable batch statistics.
- Best batch size: ~50–100 → balances noise injection and stability.
    - Large batch → less regularization effect.
    - Tiny batch → high variance, destroys useful signals.
- Makes the optimization landscape smoother.
- During prediction/inference:
    - Do not use batch statistics anymore.
    - Use fixed population statistics (computed after training from the whole dataset).

---

## 3. AdamW Optimizer

### What is AdamW?
- A stochastic gradient descent method based on adaptive estimation of first and second moments.
- Decouples weight decay from the gradient update.

---

### Core Difference from Adam:

| Feature                  | Adam                                | AdamW                              |
|--------------------------|-------------------------------------|------------------------------------|
| Weight Decay Application | Added as L2 penalty in loss        | Direct weight decay during update |
| Interaction with LR      | Can interfere with adaptive LR     | Decoupled → stable training       |
| Generalization            | May underperform on large models   | Better generalization             |
| Convergence               | Less stable for deep models        | More stable and reliable          |

---

### Practical Implications:
- Better generalization to unseen data.
- More stable convergence.
- Predictable and consistent performance.

---

### Usage Recommendations:

| Optimizer | Use When |
|-----------|----------|
| Adam      | Simple models, small datasets, replicating older implementations. |
| AdamW     | State-of-the-art tasks, deep networks, transformer architectures, large-scale datasets, regularization needed. |
