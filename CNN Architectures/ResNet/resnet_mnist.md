# ResNet Architecture on MNIST Dataset

## Model Architecture

- **Architecture:** ResNet (details below)
    - ![alt text](image.png)
- **Dataset:** MNIST
- **Optimizers Used:** Adam, AdamW

## Training Details

- **Epochs:** [Insert number of epochs]
- **Batch size:** [Insert batch size]
- **Learning Rate:** [Insert value]

## Results

| Optimizer | Validation Accuracy | Validation Loss |
|-----------|--------------------|----------------|
| Adam      | 0.9829             | 0.0200         |
| AdamW     | 0.9692             | 0.0801         |

*Adam optimizer achieved higher validation accuracy and lower validation loss compared to AdamW.*

## Visualizations

- **Validation Accuracy & Loss Graphs:**  
![alt text](resnet_val_acc.png)
![
](train_acc.png)
![alt text](train_loss.png)
![alt text](val_loss.png)
![alt text](train_result.png)
---

**Summary:**  
ResNet, when trained on MNIST, performs best with the Adam optimizer in terms of both validation accuracy and loss. Visualizations above provide a detailed comparison of performance metrics.

