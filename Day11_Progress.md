# Day 11 Progress: Concept Quiz + Expanded Notes + Model Evaluation

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
- Results: Full FT (0.493) outperformed LoRA (0.310)
- Documented hallucination patterns and repetition failure
- Pushed to GitHub

### Model Evaluation Results

| Model | Average Score |
|-------|---------------|
| LoRA 0.5B | 0.310 |
| Full Fine-Tune 0.5B | 0.493 |

### Key Findings
1. Full FT outperformed LoRA on this test
2. Both models hallucinate on unseen questions
3. Full FT had repetition failure on wifi password
4. LoRA hallucinated brand names on popular drink
5. Token overlap is crude—measures word overlap not correctness

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

## Next Steps

- FastAPI deployment
- Code practice session 5
- Continue daily concept repetition
- Consider LLM-as-judge for model evaluation
