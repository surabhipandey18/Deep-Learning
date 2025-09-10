# CIFAR-10 Image Classification

## Dataset
The **CIFAR-10 dataset** contains 60,000 32x32 color images in 10 classes:

- **Classes:** airplane, automobile, bird, cat, deer, dog, frog, horse, ship, truck  
- **Training set:** 50,000 images  
- **Test set:** 10,000 images  

Source: [CIFAR-10](https://www.cs.toronto.edu/~kriz/cifar.html)

---

## Data Preprocessing
- Images normalized to [0,1] by dividing by 255  

---


- Optimizers tested: SGD,, AdaGrad, RMSProp, Adam  
- Loss function: Categorical Crossentropy  
- Metrics: Accuracy 

## Training and Validation

- **Epochs:** 10–20  
- **Batch size:** 64–128  
- **Validation split:** 0.1  

### Example Accuracy and Loss Graphs
<img width="846" height="547" alt="image" src="https://github.com/user-attachments/assets/aa9e0373-09ce-4a90-9ff0-bb8a6ce10573" />
 
<img width="846" height="547" alt="image" src="https://github.com/user-attachments/assets/64c4224c-b438-4e1f-858a-4741b1bfdf03" />


---

## Results
<img width="507" height="116" alt="image" src="https://github.com/user-attachments/assets/ba51b117-4fcc-4581-b11c-75a8e362d8e3" />


---

## Observations
- Adam and RMSProp converge faster than plain SGD.   
- AdaGrad may stall due to shrinking learning rates.  
- CIFAR-10 requires **CNNs** for good generalization; fully connected models are baseline only.  
