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

### Capstone Phase 3: RAG Retrieval Evaluated
- Hybrid retrieval + cross-encoder reranking
- Hand-labeled relevant chunks for 10 questions
- Results:
  - Precision@10: 0.590
  - Recall@10: 0.486
  - nDCG@10: 0.660

### Capstone Phase 6: Answer Evaluation Started
- Evaluated SFT 0.5B on 200 test questions
  - Token overlap: 0.5816
  - Judge overall: 3.83
- Evaluated original distilled model
  - Token overlap: 0.4998
  - Judge overall: 3.20

### GPU Setup (ROCm on AMD 7900 XT)
- Installed torch with ROCm 10.0.0 nightly
- Fixed device selection with HIP_VISIBLE_DEVICES=1
- GPU training working, temps stable (~66-70°C)

### Capstone Phase 2b: Retrained Stronger 3B Teacher
- Trained locally on 7900 XT with stronger LoRA:
  - r=16, alpha=32, dropout=0.1
  - target modules: q_proj, k_proj, v_proj, o_proj
  - 5 epochs, lr=2e-4
- Merged to models/nimbus-sft-3b-v2-merged
- Training loss decreased steadily (2.31 -> 1.44 by epoch 0.14)

### Model Comparison (via compare-models.py)
| Model | Token Overlap | Judge Overall |
|-------|---------------|---------------|
| SFT 0.5B | 0.5816 | 3.830 |
| Teacher 3B v2 | 0.5635 | 4.035 |
| Distilled 0.5B (old) | 0.4998 | 3.200 |

Conclusion: New teacher (v2) is strongest. Old distillation used a weak teacher. Will re-distill with v2.

### Created comparison script
- `evaluation/compare-models.py` automatically evaluates models and prints table
- `evaluation/evaluate-answers.py` now supports GPU, `--output`, `--num_questions`

### Cleanup Planning
- Identified large files/folders to remove before pushing to GitHub:
  - models/ (all trained models)
  - fine-tuning/checkpoints
  - distillation output folders
  - raw generated JSONL files
  - logs, .pt, .safetensors, __pycache__
- Plan: upload models to HuggingFace, keep only code/docs/small results on GitHub
- Will execute after distillation v2 complete and evaluated

## Current Training Status
- Distillation v2 started/queued (or about to start)
- Teacher: models/nimbus-sft-3b-v2-merged
- Student: models/nimbus-sft-0.5b-final
- Output: distillation/distilled-0.5b-v2

## Next Steps
- Complete distillation v2
- Evaluate distilled-0.5b-v2
- Compare: SFT vs distilled v2 vs teacher
- If distilled v2 > SFT, success
- Then cleanup and push
- Generate DPO preference pairs
- Run DPO training on 7900 XT
- Implement security, backend, frontend
- Final evaluation and documentation

## Key Milestones
- ROCm working on local 7900 XT
- Stronger 3B teacher trained and evaluated
- Comparison pipeline automated
- Cleanup plan ready

## Honest Findings
- Original distillation failed because teacher was weak (judge 3.4 < SFT 3.83)
- Stronger teacher (v2) achieved judge 4.035
- We iterate until capstone components are genuinely solid
