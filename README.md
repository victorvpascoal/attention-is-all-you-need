# 🧠 Reproducing "Attention Is All You Need"

This repository aims to **faithfully reproduce the Transformer architecture** as proposed in the paper [*Attention Is All You Need* (Vaswani et al., 2017)](https://arxiv.org/abs/1706.03762), with two implementation approaches:

- ✅ **Manual implementation with PyTorch**
- 🔜 **Using the Hugging Face Transformers `Trainer` API**

---

## 📌 Objectives

- Replicate the original Transformer with **maximum fidelity**, including:
  - Training Byte-Pair encoding from scratch
  - Token-limited batches with approximately fixed sequence lengths
  - Shared embeddings between encoder and decoder
  - Sinusoidal positional encoding
  - Learning rate scheduler with warm-up steps and inverse square root decay
  - Adapted Beam Search decoding
- Trained on the **WMT14 English-German** translation dataset
- Evaluated on the **newstest2014** benchmark
- Training metrics and experiment tracking with **MLflow** (coming soon).

---

## 🛠️ Hardware & Training Setup
The model was trained on a single **NVIDIA GeForce RTX 4070 Super** GPU with **12GB of VRAM**. Due to memory constraints, some hyperparameters were adjusted to ensure stable training within a peak memory usage of approximately 10GB, including:

- `MAX_SEQ_LEN = 500`
- `MAX_TOKENS_PER_BATCH = 10_000`
- `WARMUP_STEPS = 10_000`
- `MAX_STEPS = 75_000`

These settings allowed the training process to remain efficient without exceeding hardware limitations.
The final model achieved a **BLEU score of 27.50** on the **newstest2014** test set.

---

## 🔗 References & Inspirations
Below are some of the key resources that inspired or guided the implementation of this project:

- [Attention Is All You Need (Vaswani et al., 2017)](https://arxiv.org/abs/1706.03762)
- [Visualize and understand GPU memory in PyTorch](https://huggingface.co/blog/train_memory)
- [How Do Self-Attention Masks Work?](https://gmongaras.medium.com/how-do-self-attention-masks-work-72ed9382510f)
- [Language Translation PyTorch's example](https://github.com/pytorch/examples/tree/main/language_translation)
- [Beam decoding](https://github.com/facebookresearch/XLM/blob/9e6f6814d17be4fe5b15f2e6c43eb2b2d76daeb4/src/model/transformer.py#L529)