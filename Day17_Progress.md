# Day 17 Progress: Capstone Phase 1 Complete + Concept Review While Training

## What I Did Today

### Concept Quiz (Separate Chat, Ongoing)
- Quizzing on all concepts while training
- Covering both core and supporting terms
- Routine repetition, no labels

### Capstone Phase 1: Data Engineering Complete
- Generated 5,333 unique Q&A pairs via DeepSeek
- Cleaned, deduplicated, validated
- Final splits:
  - SFT: 4,000 pairs -> sft_train.jsonl
  - Distillation prompts: 1,000 -> distill_prompts.jsonl
  - Test: 200 -> test_set.jsonl
- DPO preference pairs will be generated in Phase 5

### Capstone Phase 2: SFT Started
- 0.5B full fine-tune running locally on CPU
- 3B LoRA training set up in Colab (nimbus-sft-3b-lora-training.ipynb)
- Colab notebook created and named

## Current Training Status
- 0.5B: running locally (will take several hours)
- 3B LoRA: notebook ready, training or about to start on Colab T4

## Next Steps
- Complete 0.5B local training
- Complete 3B LoRA training on Colab
- Download/upload 3B model to HuggingFace
- Proceed to Phase 3: RAG system

## Projects (21 completed + capstone in progress)
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

## Key Milestones
- Data pipeline built: generate, merge, clean, split
- 5,333 unique pairs secured
- Two model training paths initiated
