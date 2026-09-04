# Day 17 Progress: Capstone Execution Begins

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

### Capstone Phase 2: SFT Complete
- 0.5B full fine-tune completed locally
  - Final loss: 0.5312
  - Saved to models/nimbus-sft-0.5b-final
- 3B LoRA trained in Colab (T4)
  - Merged into full model
  - Downloaded and extracted to models/nimbus-sft-3b-merged

### Capstone Phase 3: RAG Retrieval Evaluated
- Built hybrid retrieval + cross-encoder reranking
- Hand-labeled relevant chunks for 10 questions via review sheet
- Results (precision@10, recall@10, nDCG@10):
  - Precision: 0.590
  - Recall: 0.486
  - nDCG: 0.660

### Capstone Phase 6: Answer Evaluation Started
- Evaluated 0.5B SFT model on 200 test questions
- Mean token overlap: 0.583
- LLM-as-judge scores mostly 4-5, some lower

### Capstone Phase 4: True Distillation Prepared and Started
- Script with KL divergence, temperature scaling, alpha blending
- Quick sanity test passed on 10 examples
- Added checkpointing and logging
- Full CPU distillation started and running overnight

### Other Prepared Items
- DPO scripts (generate-preferences.py, dpo-train.py)
- Security module files drafted
- LoRA model card prepared for nimbus-sft-3b-lora

## Current Training Status
- Full distillation running locally on CPU
- Logged to distillation/distill-output.log
- Checkpoint every 500 steps
- Expected to take many hours

## Key Metrics So Far
- SFT 0.5B loss: 0.5312
- Retrieval nDCG@10: 0.660
- SFT 0.5B answer token overlap: 0.583

## Next Steps
- Monitor distillation progress
- Generate DPO preference pairs (after distillation)
- Run DPO training
- Implement security module
- Build FastAPI backend and Streamlit frontend
- Final evaluation comparing SFT vs distilled vs DPO vs RAG

## Projects
- 21 completed prior + capstone in progress

## Key Milestones
- Data pipeline finished with proper splits
- Two models trained (0.5B full, 3B LoRA merged)
- Retrieval and answer evaluation pipelines working
- True distillation running
- Security and DPO scripts ready
