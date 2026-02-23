# LLM Text Preprocessing Fundations (Embeddings)

Implementation of Chapter 2 from *Build a Large Language Model (From Scratch)* by Sebastian Raschka.

---

## What this notebook covers

- Text tokenization using regex and Byte Pair Encoding (BPE)
- Building a vocabulary and mapping tokens to integer IDs
- Special tokens: `<|endoftext|>` and `<|unk|>`
- Sliding window data sampling for next-token prediction
- Token embeddings and positional embeddings
- Experiment: how max_length and stride affect the number of training samples

---

## Files

- `embeddings.ipynb` — main notebook with code and explanations
- `the-verdict.txt` — sample text used throughout the notebook

---

## Installation
```bash
pip install torch tiktoken
```

---

## How to run
```bash
jupyter notebook embeddings.ipynb
```

Run all cells from top to bottom.

---

## References

- [Build a Large Language Model (From Scratch) — Sebastian Raschka](https://github.com/rasbt/LLMs-from-scratch)
