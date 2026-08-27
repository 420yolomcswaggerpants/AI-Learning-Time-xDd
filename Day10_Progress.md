# Day 10 Progress: Concept Quiz + Three From-Scratch Projects

## What I Did Today

### Concept Quiz + Physical Note Writing (New + Original Core Concepts)

Quizzed on all new concepts and original core concepts, and wrote them in physical notebook.

### New Core Concepts (Quizzed + Written)
- Two-stage retrieval
- Cross-encoder
- Query expansion
- Precision vs recall
- Chunking strategy

### New Supporting Concepts (Quizzed + Written)
- Bi-encoder vs cross-encoder
- First-stage retrieval
- Candidate pool
- Retrieval variance
- Negative results

### Original Core Concepts (Quizzed + Written)
- RAG
- Embeddings
- Fine-tuning vs RAG (took two attempts)
- Overfitting
- Gradient descent
- Cosine similarity
- Hybrid search
- Reciprocal rank fusion
- BM25
- Vector normalization
- Coverage vs quality
- Evaluation

### Project 11: Own Training Loop
- Wrote custom PyTorch training loop without HuggingFace Trainer
- Learned: forward pass, backward pass, gradient accumulation, optimizer step
- Tested 4 configurations (batch size 8, batch size 1 + accumulation, different learning rates)
- Finding: Trainer generalizes better because it handles schedulers, weight decay, gradient clipping
- Loss as low as 0.037 but model gave generic answers—memorization not understanding
- Pushed to GitHub

### Project 12: Attention From Scratch
- Implemented attention mechanism in NumPy
- Built: softmax, single-head attention, multi-head attention, scaled dot-product attention
- Implemented Q, K, V projections
- Learning: attention weights show which tokens matter most
- Pushed to GitHub

### Project 13: Tiny Transformer From Scratch
- Built full transformer block in NumPy
- Implemented: positional encoding, self-attention, feed-forward network, residual connections, layer normalization
- Learning: this is the architecture that powers ChatGPT, Claude, DeepSeek
- Pushed to GitHub

### New Concepts Identified (to write in notebook tomorrow)
- Query, Key, Value (QKV)
- Self-attention
- Residual connections
- Layer normalization
- Positional encoding
- Feed-forward network in transformers
- Training loop
- Gradient accumulation
- Forward and backward pass

### Major Shift
Went from API wrappers to implementing core AI architecture from scratch. Projects 11-13 are real AI engineering—training loops, attention mechanisms, transformer architectures.

## What I Learned

1. Training loop: forward pass, loss, backward pass, weight update
2. Batch size 8 overfits; gradient accumulation helps but still overfits on 80 examples
3. Loss 0.037 = memorization, not understanding
4. Attention: Q is what you look for, K is what tokens offer, V is what gets returned
5. Multi-head attention captures different patterns in parallel
6. Transformers use residual connections to help gradients flow
7. Layer norm keeps values stable
8. Positional encoding adds word order to parallel processing
9. Trainer exists for a reason—it handles details that are easy to miss

## Projects Now (13 total)

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

## Next Steps

- Write 9 new concepts in notebook tomorrow
- Add new concepts to daily quiz rotation
- Code practice session 5
- Model evaluation (perplexity, task accuracy)
- FastAPI deployment
- Continue daily concept repetition
