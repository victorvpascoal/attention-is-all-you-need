# 🧠 Reproducing "Attention Is All You Need"

This repository aims to **faithfully reproduce the Transformer architecture** as proposed in the paper [*Attention Is All You Need* (Vaswani et al., 2017)](https://arxiv.org/abs/1706.03762), with two implementation approaches:

- ✅ **Manual implementation with PyTorch**
- 🔜 **Using the Hugging Face Transformers `Trainer` API**

---

## 📌 Objectives

- Replicate the original Transformer with **maximum fidelity**, including:
  - 
  - Creating batches with limited number of tokens and approximate sequence length
  - Shared embeddings for encoder and decoder
  - Sinusoidal positional encoding
  - Learning rate scheduler with warm-up steps and inverse square root decay
- Train the model on the **WMT14 English-German** translation dataset.
- Evaluating the model on newstest2014 (coming soon).
- Track training metrics and experiments via **MLflow** (coming soon).