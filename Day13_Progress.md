# Day 13 Progress: Synthetic Data Fine-Tuning + Neural Network Fundamentals

## What I Did Today

### Project 16: Synthetic Data Fine-Tuning
- Used DeepSeek to generate 490 Q&A pairs
- Fine-tuned Qwen 2.5 0.5B on synthetic data
- Pushed to GitHub

### Model Evaluation Results (with caveats)

| Model | Score |
|-------|-------|
| Synthetic 490 examples | 0.590 |
| Full FT 0.5B (80 examples) | 0.493 |
| LoRA 3B (GPU, 4-bit) | 0.429 |
| LoRA 0.5B (80 examples) | 0.310 |

### Evaluation Caveats
- Token overlap is crude—measures shared words, not correctness
- Small test set (5 questions)
- Single-run testing—generation randomness means results could shift
- Synthetic model hallucinated with confidence (detailed but fabricated answers)
- Proper evaluation would need larger test set and better metrics
- Cannot definitively claim synthetic model is "best"—only that it scored highest on this specific test

### Project 17: ANN From Scratch
- Built neural network in NumPy with manual backpropagation
- Learned XOR successfully
- Implemented cross-entropy loss
- Implemented Adam optimizer from scratch
- Compared MSE vs CE vs Adam

### Key Concepts Learned

1. **Neurons** — computation units that take inputs, multiply by weights, add bias, apply activation
2. **Sigmoid** — squashes values to [0,1], non-linear
3. **Backpropagation** — chain rule traces error backward to compute gradients
4. **Cross-entropy loss** — logarithmic penalty, better than MSE for classification
5. **Adam optimizer** — momentum + adaptive learning rates + bias correction

### Training Results Comparison (XOR)

| Epoch | MSE + GD | CE + GD | CE + Adam |
|-------|----------|---------|-----------|
| 0 | 0.283190 | 0.762777 | 0.762777 |
| 1000 | 0.008828 | 0.093909 | 0.007382 |
| 9000 | 0.000002 | 0.001257 | 0.000036 |

### Honest Assessment
- Do NOT deeply understand the math yet
- Understand mechanics and concepts
- Math depth will come with more implementation
- Current level sufficient for junior roles
- Need to be careful about claiming "best" without proper evaluation

## Projects (17 total)

1. Email Generator (API wrapper)
2. Support Agent (API wrapper with RAG)
3. DocuBot (basic RAG)
4. Nimbus Coffee Fine-Tune (LoRA)
5. Semantic DocuBot (embeddings + dot product)
6. Hybrid RAG (cosine similarity + BM25 + RRF)
7. RAG Evaluation Harness (precision, recall, nDCG)
8. Nimbus Full Fine-Tune (comparison study)
9. Reranking RAG (two-stage retrieval)
10. Query Expansion RAG (multi-query retrieval)
11. Own Training Loop (PyTorch from scratch)
12. Attention From Scratch (NumPy)
13. Tiny Transformer (full architecture in NumPy)
14. Model Evaluation (held-out test set)
15. FastAPI Model Serving (production API)
16. Synthetic Data Fine-Tuning (490 examples)
17. ANN From Scratch (backpropagation, CE, Adam)

## Models on HuggingFace (5 total)

1. nimbus-coffee-assistant (3B LoRA)
2. nimbus-coffee-assistant-0.5b (0.5B LoRA)
3. nimbus-full-finetune-0.5b (0.5B Full FT)
4. nimbus-gpu-3b-lora (3B LoRA, GPU)
5. nimbus-distilled (0.5B, 490 synthetic examples)

## Next Steps (Tomorrow)

- Project 18: Deep Neural Network (3-4 hidden layers)
- Then Project 19: MNIST Classification
- Then Project 20: Full Transformer Training
- Then Project 21: RLHF and Reward Models
- Improve evaluation rigor (larger test sets, better metrics)

## Key Milestones

1. First neural network from scratch
2. First backpropagation implementation
3. First Adam optimizer implementation
4. Understood distinction between MSE and cross-entropy
5. Identified math depth as honest gap
6. Learned to caveat evaluation claims
