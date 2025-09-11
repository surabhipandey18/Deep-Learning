# Optimizers  

While working, I studied 5 key optimizers: **SGD, SGD + Momentum, AdaGrad, RMSProp, and Adam**.

---

### Stochastic Gradient Descent (SGD)  
The most basic optimizer — it often takes the longest to converge but is simple and efficient.  

**Mathematical Formulation:**  
$\theta_{t+1} = \theta_t - \eta \, \nabla_\theta J(\theta_t; x^{(i)}, y^{(i)})$

Where:  
- $\theta$ = model parameters  
- $\eta$ = learning rate  
- $J(\theta)$ = loss function  
- $\nabla_\theta J$ = gradient of loss w.r.t parameters  
- $(x^{(i)}, y^{(i)})$ = sample or mini-batch  

**Notes:**  
- Updates weights frequently (per sample or mini-batch).  
- Works well with large datasets.  
- With good tuning, can sometimes generalize better than adaptive methods like Adam.  

**Pros**: Simple, efficient  
**Cons**: Converges slowly, sensitive to learning rate  

---

### SGD with Momentum  
Momentum improves SGD by accelerating convergence in relevant directions and reducing oscillations.  

**Mathematical Formulation:**  

Velocity update: $v_t = \gamma v_{t-1} + \eta \, \nabla_\theta J(\theta_t)$  

Parameter update: $\theta_{t+1} = \theta_t - v_t$  

Where:  
- $v_t$ = velocity (accumulated gradient update)  
- $\gamma$ = momentum coefficient (commonly 0.9)  
- $\eta$ = learning rate  
- $\nabla_\theta J(\theta_t)$ = gradient of loss at step $t$  

**Notes:**  
- Faster learning compared to plain SGD.  
- Momentum can sometimes **“blindly ignore” sudden variations or outlier samples**, potentially increasing loss.  

**Pros**: Faster convergence, reduces oscillations  
**Cons**: Needs careful tuning of momentum ($\gamma$); may overshoot or ignore important sample signals  

---

### AdaGrad (Adaptive Gradient)  
AdaGrad adapts the learning rate for each parameter based on the historical sum of squared gradients.  

**Mathematical Formulation:**  
$\theta_{t+1} = \theta_t - \frac{\eta}{\sqrt{G_t + \epsilon}} \, \nabla_\theta J(\theta_t)$  

Where $G_t$ is the sum of squares of past gradients for each parameter, and $\epsilon$ is a small value to avoid division by zero.  

**Notes:**  
- Parameters with frequently large gradients get smaller updates, rare features get larger updates.  
- Learning rate continuously shrinks, which may **stall training** on long runs.  

**Pros**: Adapts learning rates automatically  
**Cons**: Learning rate may shrink too much, slowing/stopping training  

---

### RMSProp  
RMSProp is an improvement over AdaGrad that addresses its rapidly decreasing learning rate problem.  

**Mathematical Formulation:** 

$E[g^2]_t = \beta E[g^2]_{t-1} + (1-\beta) (\nabla_\theta J(\theta_t))^2$  

$\theta_{t+1} = \theta_t - \eta / \sqrt{E[g^2]_t + \epsilon} \cdot \nabla_\theta J(\theta_t)$


**Notes:**  
- Suitable for sequential and non-stationary data.  
- Dampens oscillations and helps with vanishing/exploding gradients.  
- Offers **faster, more stable convergence** compared to AdaGrad.  

**Pros**: Stabilizes training, reduces oscillations, flexible learning rate  
**Cons**: Parameter tuning required; careful selection of decay factor  

---

### Adam (Adaptive Moment Estimation)  
Adam combines RMSProp and Momentum for fast, robust, and adaptive learning.  

**Mathematical Formulation:**  
- Compute biased first moment estimate: $m_t = \beta_1 m_{t-1} + (1-\beta_1) \nabla_\theta J(\theta_t)$  
- Compute biased second raw moment estimate: $v_t = \beta_2 v_{t-1} + (1-\beta_2) (\nabla_\theta J(\theta_t))^2$  
- Bias-corrected updates: $\hat{m}_t = \frac{m_t}{1-\beta_1^t}, \quad \hat{v}_t = \frac{v_t}{1-\beta_2^t}$  
- Parameter update: $\theta_{t+1} = \theta_t - \frac{\eta}{\sqrt{\hat{v}_t} + \epsilon} \hat{m}_t$  

**Notes:**  
- Widely used in deep learning, large/noisy datasets.  
- Fast convergence and adaptive learning rates.  
- May underperform SGD in generalization for some tasks.  

**Pros**: Fast convergence, robust to noise, adaptive  
**Cons**: Sensitive to hyperparameters; may generalize worse than SGD  

---

### Which Optimizer to Choose?  
- Depends on the problem: image segmentation, semantic analysis, machine translation, etc.  
- Best optimizer is the one that **traverses the loss landscape effectively for your specific task**.  
- Experimentation is key — try a few and compare validation performance.

