#  Residual Networks (ResNet) and ResNeXt

_Source: [d2l.ai Chapter 8.6 - ResNet](https://d2l.ai/chapter_convolutional-modern/resnet.html)_

---

## What are Residual Networks?

- As networks deepen, it becomes **harder to ensure that added layers improve expressiveness** and model quality.
- **Nested function classes**: If larger function classes contain the smaller ones, adding more layers can only make the network **more expressive**.
- **Key idea (He et al., 2016)**: Make it easy to learn the **identity function** in any added layer, ensuring that deeper networks are at least as good as shallow ones.

---

## Why Residual Blocks?

- In plain blocks, layers must learn the full mapping \( f(x) \).
- In a **residual block**, layers learn the **residual** \( f(x) = H(x) + x \), where \( x \) is the input and \( H(x) \) the learned transformation.
- If the identity is optimal, residual learning makes it easier for the network to just “pass through” inputs.
- **Residual/shortcut connection:** The input is added to the block’s output before activation.

**Residual Block Pseudocode (TensorFlow):**

class Residual(tf.keras.Model):
def init(self, num_channels, use_1x1conv=False, strides=1):
super().init()
self.conv1 = tf.keras.layers.Conv2D(num_channels, 3, strides=strides, padding='same')
self.conv2 = tf.keras.layers.Conv2D(num_channels, 3, padding='same')
self.bn1 = tf.keras.layers.BatchNormalization()
self.bn2 = tf.keras.layers.BatchNormalization()
self.conv3 = tf.keras.layers.Conv2D(num_channels, 1, strides=strides) if use_1x1conv else None


---

## ResNet Architecture

- First layers like GoogLeNet: Conv (64, kernel 7x7, stride 2) + BatchNorm + ReLU + MaxPool (3x3, stride 2)
- **Four residual modules:** Each with multiple residual blocks
  - Channels double and spatial size halves at each new module (via stride or 1x1 conv)
- **Output:** Global average pooling, then a dense (fully connected) layer

**Example: ResNet-18 Block Structure**
- Each block: 2 residual blocks × 4 modules = 8 main residual blocks + initial/final layers


---

## Training and Properties

- ResNet shows a gap between training/validation loss: **more data helps**.
- Deeper variants: ResNet-18, ResNet-34, up to ResNet-152.
- **Residual connections accelerate training** and enable extremely deep networks.

---

## ResNeXt

- **Motivation:** Tradeoff between depth/nonlinearity and width/dimensionality.
- **Key idea:** Use **grouped convolution**—channels are split into groups and convolutions are applied independently, then merged.
- Grouped convolution is **much faster** and uses **fewer parameters**.
- ResNeXt blocks sandwich grouped 3x3 convolutions between 1x1 convs for efficient channel management.


---

## Summary

- **Residual connections** allow deeper networks to be trained by making it easy to learn the identity mapping.
- **ResNet**: Simpler and more flexible than previous deep CNNs, enabling rapid adoption and stacking of very deep networks.
- **ResNeXt**: Evolved by incorporating grouped convolutions for efficiency and scalability.
- Residual-style connections have become foundational for modern architectures, including **Transformers** in NLP and Vision.

---

**Tip:** For more implementation details and live code, see the original [d2l.ai ResNet chapter](https://d2l.ai/chapter_convolutional-modern/resnet.html).

