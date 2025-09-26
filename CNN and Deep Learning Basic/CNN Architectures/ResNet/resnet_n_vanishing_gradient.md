## Skip Connections
### What are skip connections?
- Connections that “skip over” one or more layers, passing input forward directly.
- First popularized by **ResNet** (He et al., 2015).

### Why are they useful?
- Help preserve gradients during backpropagation → mitigate **vanishing gradient problem**.
- Allow networks to train deeper models by enabling identity mapping.
- Intuitively: the network can "choose" to learn an identity function or a residual function.

### Example (ResNet Block)
Input: `x`  
Layer: `F(x)`  
Output with skip connection: `y = F(x) + x`

---

## Convolution as a Linear Operator
### Reminder
- Convolution is a **linear transformation**: scaling and adding.
- Each convolution filter is like a structured matrix multiplication (Toeplitz matrix).

### Math Derivation
For 1D signals:
\[
(y * w)[n] = \sum_{k} x[n-k] w[k]
\]

For 2D images:
\[
Y[i,j] = \sum_{m} \sum_{n} X[i-m, j-n] \, W[m,n]
\]

Matrix form:  
- Flatten the input image into a vector.  
- Represent convolution kernel as a **sparse Toeplitz matrix**.  
- Then:  
\[
\mathbf{y} = \mathbf{Kx}
\]  
where \( \mathbf{K} \) encodes the convolution weights.

---

## Vanishing Gradient Problem
### What is it?
- In deep networks, gradients shrink exponentially as they propagate backward.
- Small gradients → earlier layers learn extremely slowly.

### Why does it happen?
- Activation functions like sigmoid/tanh have derivatives < 1.
- Chain rule multiplies many small derivatives across layers.
- Leads to weights in lower layers barely updating.

### Why skip connections help
- They provide **shorter gradient paths**, reducing shrinkage.
- Ensure that even deep networks can learn meaningful features.
