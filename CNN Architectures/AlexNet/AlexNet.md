# Deep CNN: AlexNet

AlexNet represents a significant improvement over LeNet, introducing deeper architectures and new techniques to advance convolutional neural networks.

---

## Overview

- **AlexNet** is an 8-layer CNN, which marked a major breakthrough in feature learning compared to previous hand-crafted designs.
- It allowed **features obtained by learning to surpass manually designed features** for the first time.

---

## AlexNet Structure
<img width="552" height="711" alt="image" src="https://github.com/user-attachments/assets/f8dfdd94-97e6-490e-85c2-c5e2563e9798" />


- **Activation Function:** Uses **ReLU** instead of sigmoid.
  - Earlier networks (like LeNet) used the **sigmoid** activation, where outputs were close to 0 or 1. This caused near-zero gradients in those regions, making backpropagation ineffective for some parameters (vanishing gradient problem).
  - In contrast, **ReLU** has a gradient of 1 in the positive interval, thus avoiding this issue and allowing faster, more effective training.

- **Regularization:**
  - **Dropout** is used in AlexNet, leading to better accuracy and easier training.
  - LeNet used **weight decay** for regularization and sigmoid as the activation, which was less effective.

- **Overfitting:** 
  - AlexNet is highly resistant to overfitting. **Training and validation loss remain almost identical throughout**, thanks to improved regularization (dropout).

---

**Summary:**  
AlexNet’s use of deeper architectures, ReLU activations, and dropout regularization resulted in a leap forward in practical performance and generalization, compared to older networks like LeNet.

source: https://d2l.ai/chapter_convolutional-modern/alexnet.html
