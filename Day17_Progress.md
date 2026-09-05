# Day 17 Progress: Capstone Execution + GPU Training + Cleanup Planning

## What I Did Today

### Concept Quiz (Separate Chat, Ongoing)
- Quizzing on all concepts while training and building
- Routine repetition, no labels

### Capstone Phase 1: Data Engineering Complete
- Generated 5,333 unique Q&A pairs via DeepSeek
- Cleaned, deduplicated, validated
- Final splits:
  - SFT: 4,000 pairs -> sft_train.jsonl
  - Distillation prompts: 1,000 -> distill_prompts.jsonl
  - Test: 200 -> test_set.jsonl

### Capstone Phase 2: SFT Models
- 0.5B full fine-tune completed locally
  - Final loss: 0.5312
  - Saved to models/nimbus-sft-0.5b-final
- Original 3B LoRA trained in Colab (T4)
  - Merged to models/nimbus-sft-3b-merged

### Capstone Phase 2b: Retrained Stronger 3B Teacher (v2)
- Trained locally on 7900 XT with stronger LoRA:
  - r=16, alpha=32, dropout=0.1
  - target_modules: q_proj, k_proj, v_proj, o_proj
  - 5 epochs, lr=2e-4
- Merged to models/nimbus-sft-3b-v2-merged
- Training loss decreased steadily

### Capstone Phase 3: RAG Retrieval Evaluated
- Hybrid retrieval + cross-encoder reranking
- Hand-labeled relevant chunks for 10 questions
- Results:
  - Precision@10: 0.590
  - Recall@10: 0.486
  - nDCG@10: 0.660

### Capstone Phase 6: Answer Evaluation
- Evaluated SFT 0.5B on 200 test questions
  - Token overlap: 0.5816
  - Judge overall: 3.830
- Evaluated original distilled model (weak teacher)
  - Token overlap: 0.4998
  - Judge overall: 3.200
- Evaluated new teacher (3B v2)
  - Token overlap: 0.5635
  - Judge overall: 4.035
- Evaluated distilled v2 (from v2 teacher)
  - Token overlap: 0.5524
  - Judge overall: 3.605

### Model Comparison Summary
| Model | Token Overlap | Judge Overall |
|-------|---------------|---------------|
| SFT 0.5B | 0.5816 | 3.830 |
| Teacher 3B v2 | 0.5635 | 4.035 |
| Distilled 0.5B v2 | 0.5524 | 3.605 |

Conclusion: Teacher v2 is best on judge quality, but distillation from it did not beat SFT baseline. Distillation implemented correctly but failed to improve the 0.5B student. This is a documented negative result.

### GPU Setup (ROCm on AMD 7900 XT)
- Installed torch with ROCm 10.0.0 nightly
- Fixed device selection with HIP_VISIBLE_DEVICES=1
- GPU training working, temps stable (~66-70°C)

### Created comparison script
- `evaluation/compare-models.py` automatically evaluates models and prints table
- `evaluate-answers.py` now supports GPU, `--output`, `--num_questions`

### Cleanup Planning
- Identified large files/folders to remove before pushing to GitHub:
  - models/ (all trained models)
  - fine-tuning/checkpoints
  - distillation output folders
  - raw generated JSONL files
  - logs, .pt, .safetensors, __pycache__
- Plan: upload models to HuggingFace, keep only code/docs/small results on GitHub
- Will execute after final model selection and evaluation

## Current Status
- Distillation v2 complete and evaluated; did not beat SFT baseline
- Decision: move to DPO on SFT 0.5B tomorrow
- Preference generation and DPO training scripts ready

## Next Steps
- Generate DPO preference pairs
- Train DPO on SFT 0.5B using 7900 XT
- Evaluate DPO model vs SFT and distilled v2
- If DPO improves, select best model for final system
- Cleanup and push to GitHub
- Implement security, backend, frontend
- Final evaluation and documentation

## Key Milestones
- ROCm working on local 7900 XT
- Stronger 3B teacher trained and evaluated
- Comparison pipeline automated
- True distillation attempted twice, documented honest negative result
- DPO as final alignment path

## Honest Findings
- Distillation did not improve 0.5B student despite correct KL divergence implementation
- Teacher v2 has best judge quality, but student cannot fully capture it
- SFT 0.5B remains strong baseline (judge 3.83)
- Moving to DPO to improve baseline further
