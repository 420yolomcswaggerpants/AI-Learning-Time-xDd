# Day 12 Progress: GPU Training + Model Evaluation + FastAPI

## What I Did Today

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

### First GPU Training (Google Colab)
- Set up Colab with T4 GPU
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
5. Colab T4 is limited (14.5GB VRAM) but workable for LoRA on quantized models

### Project 15: FastAPI Model Serving
- Built production-style API for serving fine-tuned model
- POST /answer endpoint returns model-generated answers as JSON
- GET /health endpoint for monitoring
- Automatic API documentation at /docs
- Pydantic validation for request/response
- Pushed to GitHub

### FastAPI vs Streamlit
- Streamlit = demos
- FastAPI = production
- FastAPI endpoints can be called by any application
- FastAPI supports authentication, rate limiting, load balancing

## Models on HuggingFace (4 total)

1. nimbus-coffee-assistant (3B LoRA, CPU)
2. nimbus-coffee-assistant-0.5b (0.5B LoRA, CPU)
3. nimbus-full-finetune-0.5b (0.5B Full FT, CPU)
4. nimbus-gpu-3b-lora (3B LoRA on 4-bit, GPU)

## Projects Now (15 total)

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
14. Model Evaluation (held-out test set)
15. FastAPI Model Serving (production API)

## Next Steps

- Real dataset project (bigger than 80 synthetic Q&As)
- Read "Attention Is All You Need" deeply
- Continue daily concept quiz
- Code practice session 5
- Consider Python 3.12 for 7900 XT ROCm support

## Key Milestones

1. First GPU training completed (Colab T4)
2. First production API built (FastAPI)
3. First multi-model evaluation completed
4. Learned that bigger model + quantization ≠ better results
