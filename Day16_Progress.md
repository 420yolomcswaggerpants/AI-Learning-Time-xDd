# Day 16 Progress: Concept Review + Capstone Blueprint (Final, Corrected)

## What I Did Today

### Concept Quiz (Separate Chat)
- Quizzed on Day 15 concepts (MNIST + RLHF)
- Wrote all Day 15 concepts in notebook and Google Doc

### Day 15 Concepts Added to Rotation
**MNIST:**
- Softmax
- One-hot encoding
- Multi-class cross-entropy
- Image normalization

**RLHF:**
- RLHF (Reinforcement Learning from Human Feedback)
- Policy Gradient
- REINFORCE algorithm
- Reward Shaping
- Exploration vs Exploitation
- Local Optimum
- Supervised Pretraining Before RL
- Entropy Bonus
- RLHF Workflow (Supervised Fine-Tuning → RL)

### Capstone Planning: Nimbus AI Support Platform
- Committed to generalist capstone integrating all major skills
- Built final corrected blueprint with true distillation, DPO, data engineering, evaluation, security, engineering, and deployment
- Acknowledged earlier mistakes: text-generation was mislabeled as distillation; now fixed with true KL divergence distillation
- Added DPO (Direct Preference Optimization) for practical RLHF
- Added data engineering, data splits, testing, fallbacks, experiment tracking, reproducibility

## Capstone Blueprint: Nimbus AI Support Platform

### Phase 1: Data Engineering & Preparation
- Generate 5,000 Q&A pairs via DeepSeek API
- Clean: remove duplicates, strip whitespace, validate JSON, filter malformed entries
- Split datasets:
  - SFT Set: 4,000 pairs (labeled)
  - Distillation Set: 1,000 prompts (unlabeled)
  - DPO/Reward Set: 500 preference pairs (chosen vs rejected)
  - Test Set: 200 held-out pairs (never used in training)

### Phase 2: Supervised Fine-Tuning (SFT)
- Model 1: Fine-tune 0.5B full on local CPU
- Model 2: Fine-tune 3B LoRA on Colab T4
- Log hyperparameters, loss curves, save artifacts

### Phase 3: RAG System
- Hybrid search: semantic embeddings + BM25
- Reciprocal Rank Fusion (RRF) implemented from scratch
- Cross-encoder reranking
- Fallback if retrieval score below threshold

### Phase 4: True Knowledge Distillation
- Teacher: 3B SFT model (local)
- Student: 0.5B SFT model
- Process:
  1. Teacher generates logits on the 1,000 Distillation Set prompts
  2. Apply temperature scaling to teacher softmax
  3. Train student with KL Divergence Loss to match teacher probability distribution
- Result: 0.5B student learns teacher's confidence and behavior

### Phase 5: RLHF & Reward Training
- Reward Model: Train classifier to score responses
- Algorithm A (Mechanics Demo): REINFORCE on small LSTM policy (already built in Project 21)
- Algorithm B (Production): Apply DPO to 0.5B model using 500 preference pairs
- DPO is stable, no separate reward model needed during training

### Phase 6: Evaluation Suite
- Retrieval: Precision@k, Recall@k, nDCG
- Answer Quality: LLM-as-Judge (DeepSeek API)
- A/B Testing: SFT vs Distilled vs DPO vs RAG
- Produce comprehensive ranking report

### Phase 7: Security Hardening (Blue Team)
- Threat model: prompt injection, PII leakage, denial of service
- Input validation: sanitize, limit length, block control characters
- Prompt injection defense: instruction hierarchy, delimiter patterns, input tagging
- Output filtering: PII regex, harmful content checks
- Rate limiting: token bucket per IP
- Audit logging: queries, model versions
- Adversarial prompt test suite

### Phase 8: Deployment & Engineering
- Backend: FastAPI with security middleware, graceful fallbacks
- Frontend: Streamlit chat interface
- Reproducibility: Dockerfile, pinned requirements, setup README
- Live demo: 0.5B distilled model + RAG on free hosting
- Documentation: architecture diagram, design tradeoffs, security considerations

## Verification Against Requirements

| Component | Included? |
|-----------|-----------|
| SFT | Yes, Phase 2 |
| True Distillation (KL divergence) | Yes, Phase 4 |
| RLHF | Yes, Phase 5 |
| Reward training | Yes, Phase 5 |
| REINFORCE algorithm | Yes, Phase 5 |
| Policy gradient | Yes, Phase 5 (as part of REINFORCE) |
| RAG | Yes, Phase 3 |
| Evaluation | Yes, Phase 6 |
| Deployment | Yes, Phase 8 |
| Security / Blue team | Yes, Phase 7 |
| Data engineering | Yes, Phase 1 |
| Testing | Yes, Phase 7 + Phase 6 |
| Fallbacks | Yes, Phase 3 + Phase 8 |
| Experiment tracking | Yes, Phase 2 |
| Reproducibility | Yes, Phase 8 |

## Projects Now (21 completed + 1 capstone in progress)

1. Email Generator
2. Support Agent
3. DocuBot
4. Nimbus Coffee Fine-Tune (LoRA)
5. Semantic DocuBot
6. Hybrid RAG
7. RAG Evaluation Harness
8. Nimbus Full Fine-Tune
9. Reranking RAG
10. Query Expansion RAG
11. Own Training Loop
12. Attention From Scratch
13. Tiny Transformer
14. Model Evaluation
15. FastAPI Model Serving
16. Synthetic Data Fine-Tuning
17. ANN From Scratch
18. Deep Neural Network From Scratch
19. MNIST Classifier From Scratch
20. Transformer Training
21. RLHF Simulation

## Next Steps

- Execute Phase 1: Data Generation & Cleaning
- Create folder structure
- Run generate-data.py for 5,000 pairs
- Clean and split data
- Continue daily concept quiz

## Key Milestones

1. 21 projects in 16 days
2. Final capstone blueprint corrected and verified
3. True distillation and DPO added
4. Security, data engineering, testing, fallbacks, reproducibility all included
