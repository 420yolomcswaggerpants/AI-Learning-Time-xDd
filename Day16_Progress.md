# Day 16 Progress: Concept Review + Capstone Blueprint (Complete)

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
- Decided on a generalist capstone that integrates all major skills
- Full blueprint created covering SFT, RAG, distillation, RLHF, evaluation, deployment, and security
- Commitment to include blue teaming / security hardening as a full module
- Model strategy: 0.5B for live demo (Streamlit), 3B LoRA for scale (HuggingFace)

## Capstone Blueprint: Nimbus AI Support Platform

### Phase 1: Data & SFT (Supervised Fine-Tuning)
- Generate 5,000 synthetic Q&A pairs via DeepSeek
- Format instruction/response
- Fine-tune 0.5B full (local CPU or Colab)
- Fine-tune 3B LoRA (Colab T4, save to HuggingFace)
- Save both models

### Phase 2: RAG System
- Hybrid search (semantic + BM25 + RRF)
- Cross-encoder reranking
- Integrate with fine-tuned models

### Phase 3: Distillation
- DeepSeek API as teacher
- Train student 0.5B on teacher outputs (text distillation)
- Compare student vs SFT-only vs teacher

### Phase 4: RLHF / Policy Gradient / REINFORCE
- Build reward model (classifier or rule-based)
- Train small LSTM policy with REINFORCE + entropy bonus
- Demonstrate full RLHF loop (SFT → reward → RL)
- Optionally apply policy gradient to 0.5B SFT model

### Phase 5: Evaluation Suite
- Retrieval metrics: precision, recall, nDCG
- Answer quality: LLM-as-judge
- A/B comparisons: SFT vs Distilled vs RLHF-tuned vs RAG-only
- Report findings

### Phase 6: Security Hardening (Full Blue Team Module)
- Input validation & sanitization
- Prompt injection defenses (instruction hierarchy, delimiter patterns)
- Output filtering (PII, harmful content, confidence threshold)
- Rate limiting (token bucket per IP)
- Audit logging
- Secrets management & rotation
- Threat model document (attack matrix)
- Adversarial prompt test suite

### Phase 7: Deployment & Integration
- FastAPI backend with security middleware
- Streamlit frontend
- Live demo: 0.5B + RAG on Streamlit Cloud (free)
- 3B model on HuggingFace with run instructions
- Model versioning

### Phase 8: Documentation
- Architecture diagram
- Design decisions and tradeoffs
- Security considerations
- Evaluation results
- Lessons learned

## Verification Against User Requirements

| Requested Component | Included? |
|---------------------|-----------|
| SFT | Yes, Phase 1 |
| Distillation | Yes, Phase 3 |
| RLHF | Yes, Phase 4 |
| Reward training | Yes, Phase 4 |
| REINFORCE algorithm | Yes, Phase 4 |
| Policy gradient | Yes, Phase 4 |
| RAG | Yes, Phase 2 |
| Evaluation | Yes, Phase 5 |
| Deployment | Yes, Phase 7 |
| Blue teaming / security | Yes, Phase 6 |
| From-scratch component | Partial: we may implement custom training loop or RRF, but could add explicit from-scratch module if needed |

**Note:** The capstone currently uses PyTorch/HuggingFace for training, which is production-appropriate. A from-scratch component is not strictly required for a generalist capstone, but if we want to include it, we can add a custom RRF implementation or a small custom evaluation metric. Let me know if you want to add that.

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

- Start Capstone Phase 1: Data Generation
- Run generate-data.py with 5,000 pairs
- Prepare Colab notebook for 3B LoRA training
- Continue daily concept quiz

## Key Milestones

1. 21 projects in 16 days
2. Capstone blueprint finalized with all requested components
3. Security hardening included as full module
4. Clear phased plan for next several days
