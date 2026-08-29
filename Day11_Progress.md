# Day 11 Progress: Concept Quiz + Expanded Notes + Model Evaluation + GPU Training

## What I Did Today

### Concept Quiz (Separate Chat)
- Quizzed on all 41 concepts using handoff prompt
- Covered core + supporting concepts
- Quiz format: answer in own words, guided when wrong

### Note Expansion
Added detailed notes under each concept with deeper context:

### Core Concept Additions
- **Overfitting**: solutions (more data, regularization, early stopping, simpler model, data augmentation), diagnostic pattern (training loss falls while validation loss rises)
- **Gradient descent**: mechanics of negative gradient direction, learning rate schedules (warmup, cosine decay, step decay)
- **Cosine similarity**: range is [0,1] in practice for embeddings, why not Euclidean distance
- **RRF**: any two scoring systems can have arbitrary scales, ranks make them irrelevant
- **Vector normalization**: part of cosine similarity, not separate; normalize at index time for fast dot product at query time
- **Coverage vs quality**: coverage is about retrieving, not answering; quality is about precision in retrieved set
- **Evaluation**: why RAG evaluation is hard (multiple components, no single correct answer, retrieval vs generation metrics, LLM-as-judge noise)
- **Fine-tuning**: when to use (style, domain patterns, fixed knowledge, reduce prompt overhead); RAG and fine-tuning compose
- **RAG**: when to use (dynamic knowledge, grounding, citations, avoid retraining)
- **Hybrid search**: what keyword excels at vs what semantic excels at
- **Two-stage retrieval**: efficiency comparison (single-stage bi vs single-stage cross vs two-stage)
- **Cross-encoder**: [CLS] token classification head, full transformer forward pass
- **Query expansion**: HyDE, index-time expansion, noise risk
- **Precision vs recall**: F1 score, recall@k (what fraction of relevant chunks made it into top k)
- **Chunking strategy**: small vs large chunks tradeoff, overlap, hierarchical chunking, metadata attachment
- **Candidate pool**: recall saturation point, reranker cost, noise tolerance, latency budget

### Supporting Concept Additions
- **Tokenization**: why subword (character-level too short, word-level can't handle unknown words), BPE/WordPiece/SentencePiece
- **Attention**: difference between attention and self-attention (Q from same sequence or different)
- **Context window**: truncation behavior, everything competes for same budget, longer windows ≠ free, "lost in the middle"
- **Hallucination**: causes in RAG (missing context, noisy context, weak grounding, overly assertive prompts), mitigation vs elimination
- **Temperature**: divides logits before softmax, exploration vs exploitation dial
- **Base vs fine-tuned**: fine-tuning teaches behavior not knowledge, instruction tuning vs domain tuning
- **System vs user roles**: system messages not always obeyed, developer role in newer APIs
- **Zero-shot vs few-shot**: in-context learning, example order matters
- **Quantization**: PTQ vs QAT, GGUF/AWQ/GPTQ formats, 8-bit often negligible degradation
- **Instruction vs domain tuning**: complementary, can be stacked
- **Bi-encoder vs cross-encoder**: bi-encoders can't see interaction at encoding time, cross-encoders model fine-grained interactions
- **First-stage retrieval**: ceiling on downstream, good candidate pool properties (recall, size, low noise)
- **Retrieval variance**: causes (index updates, query reformulation, reranker non-determinism, ANN search, model updates)
- **Negative results**: prevent shipping worse system, reveal shape of problem, difference between engineering and vibes

### New From-Scratch Concept Additions
- **Self-attention**: scaling by 1/sqrt(d_k) prevents softmax saturation, keeps gradients in useful range
- **Residual connections**: highway for information, network can't get worse by adding layers
- **Layer normalization**: pre-LN vs post-LN (modern models use pre-LN), normalizes across feature dimension not batch
- **Positional encoding**: modern models use learned or RoPE instead of sine/cosine, added to token embeddings
- **Feed-forward network**: attention is how tokens talk, FFN is where thinking happens, GeLU/SwiGLU in modern models
- **Training loop**: data loading/batching, learning rate scheduling
- **Gradient accumulation**: memory tradeoff, speed cost
- **Forward/backward pass**: gradients are ∂L/∂w via chain rule, optimizer determines actual update

### New Concept Added
- **TF-IDF** (supporting): term frequency × inverse document frequency, no saturation or length control, BM25 fixes both

### Project 14: Model Evaluation
- Built evaluation framework for comparing fine-tuned models
- Created held-out test set (5 questions not in training data)
- Scored answers using token overlap against ground truth
- Tested 3 models: LoRA 0.5B, Full FT 0.5B, LoRA 3B (GPU)
- Pushed to GitHub

### Model Evaluation Results

| Model | Average Score |
|-------|---------------|
| Full FT 0.5B (CPU) | 0.493 |
| LoRA 3B (GPU, 4-bit) | 0.429 |
| LoRA 0.5B (CPU) | 0.310 |

### Google Colab GPU Training (First Time)
- Set up Google Colab with T4 GPU
- Learned: Python 3.14 has no ROCm support for 7900 XT, so Colab is temporary GPU path
- First attempt: 3B model OOM on T4
- Fix: 4-bit quantization (BitsAndBytesConfig) + LoRA adapters
- Second attempt: loss 3.02 → 2.85 (barely learned, learning rate too low)
- Fix: learning rate 5e-5 → 2e-4 (LoRA standard)
- Third attempt: loss 2.76 → 0.94 (successful)
- Model uploaded to HuggingFace: nimbus-gpu-3b-lora

### Key Findings from GPU Training
1. Quantized LoRA on 3B did NOT beat full fine-tune on 0.5B
2. Learning rate matters—2e-4 for LoRA, 5e-5 for full FT
3. Bigger model + quantization ≠ better results
4. Training method matters as much as model size

## Updated Concept Counts

- Core concepts: 26
- Supporting concepts: 16 (added TF-IDF)
- Total: 42

## Projects Now (14 total)

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
14. Model Evaluation (held-out test set, token overlap)

## Models on HuggingFace (4 total)

1. nimbus-coffee-assistant (3B LoRA, CPU)
2. nimbus-coffee-assistant-0.5b (0.5B LoRA, CPU)
3. nimbus-full-finetune-0.5b (0.5B Full FT, CPU)
4. nimbus-gpu-3b-lora (3B LoRA on 4-bit, GPU)

## Next Steps

- FastAPI deployment
- Code practice session 5
- Continue daily concept repetition
- Consider LLM-as-judge for model evaluation
- Real dataset project (bigger than 80 synthetic Q&As)

## Key Milestone

First GPU training completed. Set up Colab, handled OOM errors, implemented 4-bit quantization, tuned learning rate, and deployed a GPU-trained model to HuggingFace.
