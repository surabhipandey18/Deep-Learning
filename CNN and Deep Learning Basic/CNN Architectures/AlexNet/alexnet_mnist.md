# AlexNet on MNIST: Adam vs AdamW Optimizer Comparison

This project benchmarks the performance of the classic **AlexNet architecture** on the MNIST handwritten digit dataset, comparing two optimizers: **Adam** and **AdamW**.

## Experiment Setup

- **Dataset:** MNIST (resized to 224×224, grayscale images)
- **Model:** AlexNet (adapted for 1-channel input)
- <img width="1286" height="4589" alt="image" src="https://github.com/user-attachments/assets/59b45d09-4655-4d83-8e7e-e53cf1ebd964" />

- **Batch size:** 64
- **Epochs:** 5
- **Optimizers tested:**  
    - Adam (`learning_rate=1e-3`)
    - AdamW (`learning_rate=1e-3`, `weight_decay=1e-4`)

## Results

| Optimizer | Validation Accuracy | Validation Loss |
|-----------|---------------------|----------------|
| Adam      | 0.9868              | 0.0453         |
| AdamW     | 0.9888              | 0.1169         |

*Note:*  
- **AdamW achieved higher accuracy,** but with higher cross-entropy loss compared to Adam.
- This means AdamW produced more correct predictions, but with less "confidence" (more regularized output probabilities).

<img width="552" height="62" alt="image" src="https://github.com/user-attachments/assets/4336c9c1-bdbf-4fe9-8f0a-ca858b3f03dd" />


## Observations


- **Higher accuracy, higher loss:**  
  With AdamW, the model is more regularized, leading to correct classes being chosen, but assigned lower probabilities. This results in increased loss value but improved classification accuracy.
- **Adam showed lower loss, but marginally lower accuracy.**
<img width="855" height="547" alt="image" src="https://github.com/user-attachments/assets/b2f72949-1e59-4471-bd63-517437ac6704" />
<img width="863" height="547" alt="image" src="https://github.com/user-attachments/assets/1b146572-6227-4eeb-91fa-5a2ca2b04449" />
<img width="855" height="547" alt="image" src="https://github.com/user-attachments/assets/a1923829-c035-4de8-a8ba-7cb367084d6e" />
<img width="855" height="547" alt="image" src="https://github.com/user-attachments/assets/47ade8a3-c013-4714-b49d-42ceca6e9154" />


## Conclusion

**AdamW can provide slightly better accuracy for AlexNet on MNIST,** though with less confident predictions (as seen by the higher validation loss). For tasks where top-1 accuracy matters most, AdamW is a strong choice; if well-calibrated probabilities are also important, further tuning is recommended.

---





## Code Example (Core Training Loop)

