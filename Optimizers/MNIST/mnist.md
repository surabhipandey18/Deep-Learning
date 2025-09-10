# MNIST Handwritten Digit Classification

## Dataset
The **MNIST dataset** consists of 70,000 grayscale images of handwritten digits (0–9).  
- **Training set:** 60,000 images  
- **Test set:** 10,000 images  
- Each image is **28x28 pixels**.  
- Labels are integers from 0 to 9.  

Source: [MNIST](http://yann.lecun.com/exdb/mnist/)

---

- Optimizers tested: SGD, AdaGrad, RMSProp, Adam  
- Loss function: Sparse Categorical Crossentropy  
- Metrics: Accuracy  

---
## Training and Validation

- **Epochs:** 5 (depending on optimizer)  
- **Batch size:** 64  

### Example of Model Accuracy and Loss Graphs
<img width="855" height="547" alt="image" src="https://github.com/user-attachments/assets/74effa95-9385-4c3a-bac3-e7a29ff04ded" />
<img width="846" height="547" alt="image" src="https://github.com/user-attachments/assets/9b748e6f-4859-4026-b8a4-1eacc346ad9b" />


---

## Results

<img width="503" height="109" alt="image" src="https://github.com/user-attachments/assets/21b77971-025d-4060-8566-7a6cec090d28" />

---

## Observations
- Adam achieved the best validation accuracy.  
- RMSProp stabilizes learning for sequential and non-stationary data.  
- AdaGrad may slow down if training runs for too long.  

