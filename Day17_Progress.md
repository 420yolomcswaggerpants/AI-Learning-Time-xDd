# Day 17 Progress: Capstone Execution + GPU Setup

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
- Results:
  - Precision@10: 0.590
  - Recall@10: 0.486
  - nDCG@10: 0.660

### Capstone Phase 6: Answer Evaluation Started
- Evaluated 0.5B SFT model on 200 test questions
- Mean token overlap: 0.583
- LLM-as-judge scores mostly 4-5, some lower

### Capstone Phase 4: True Distillation
- Script with KL divergence, temperature scaling, alpha blending
- Quick sanity test passed on 10 examples
- Added checkpointing and logging
- Full distillation initially started on CPU, then moved to GPU after ROCm setup

### GPU Setup (ROCm on AMD 7900 XT)
- Installed torch with ROCm 10.0.0 from AMD nightly repo
- PyTorch now sees AMD Radeon RX 7900 XT
- Initially selected integrated graphics, fixed with HIP_VISIBLE_DEVICES=1
- Distillation now running on 7900 XT, usage ~69%

## Current Training Status
- Full distillation running on 7900 XT GPU
- Logged to distillation/distill-output-gpu.log
- Checkpoint every 500 steps
- Expected to finish in under an hour

## Key Metrics So Far
- SFT 0.5B loss: 0.5312
- Retrieval nDCG@10: 0.660
- SFT 0.5B answer token overlap: 0.583

## Next Steps
- Monitor distillation progress on GPU
- Evaluate distilled model vs SFT and teacher
- Generate DPO preference pairs
- Run DPO training on 7900 XT
- Implement security module
- Build FastAPI backend and Streamlit frontend
- Final evaluation comparing SFT vs distilled vs DPO vs RAG

## Projects
- 21 completed prior + capstone in progress

## Key Milestones
- Data pipeline finished with proper splits
- Two models trained (0.5B full, 3B LoRA merged)
- Retrieval and answer evaluation pipelines working
- True distillation running on local GPU
- ROCm setup completed for future GPU training
