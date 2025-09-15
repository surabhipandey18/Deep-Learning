# 🇮🇳 English → Hindi Translation using Transformer

This project demonstrates training and inference of a Transformer-based machine translation model on an **English-Hindi parallel corpus** using Hugging Face’s Transformers library.

---

## Dataset
- Format: CSV file
- Columns:
    - `english_sentence`: English sentence
    - `hindi_sentence`: Hindi sentence
- Example row:
    | English | Hindi |
    |---------|-------|
    | Hello, how are you? | नमस्ते, आप कैसे हैं? |

---

## Approach

1. **Data Preparation**  
   Loaded the CSV dataset and tokenized sentences using Hugging Face’s `AutoTokenizer` from the pretrained model `Helsinki-NLP/opus-mt-en-hi`.

2. **Pretrained Model Used**  
   Model: `Helsinki-NLP/opus-mt-en-hi`  
   This is a MarianMT (Marian Machine Translation) model pretrained specifically for English → Hindi translation.

3. **Model Architecture**  
   Utilizes Transformer encoder-decoder architecture with:
   - Token embeddings
   - Positional encoding
   - Multi-head self-attention layers
   - Final linear layer projecting to vocabulary logits

4. **Training**
    - Fine-tuned the pretrained model on the dataset.
    - Batch size: 8
    - Loss: Cross-Entropy
    - Optimizer: AdamW
    - Teacher forcing used during training

5. **Inference**
    - Input sentence tokenized and passed to the model.
    - Translation generated using `model.generate()`.
    - Output tokens decoded to Hindi text.

---

##  Example Result

| English Input               | Hindi Output                |
|-----------------------------|-----------------------------|
| How are you today?          | आप आज कैसे हैं?              |
| I love machine learning.    | मुझे मशीन लर्निंग पसंद है।  |
| What is your name?          | आपका नाम क्या है?            |

---

##  Key Insights

- Pretrained MarianMT models provide state-of-the-art translation quality out of the box.
- Fine-tuning helps the model adapt to your specific dataset with small compute requirements.
- Transformer architecture handles long-range dependencies better than RNNs.
- Tokenizer handles padding, truncation, and subword tokenization efficiently.

---

