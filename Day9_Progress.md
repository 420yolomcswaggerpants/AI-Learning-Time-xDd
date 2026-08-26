# Day 9 Progress: Reranking RAG + Honest Evaluation

## What I Did Today

### Project 9: Reranking RAG
- Built two-stage retrieval system
- Stage 1: Semantic search finds top 20 candidates
- Stage 2: Cross-encoder reranks to top 10
- Used cross-encoder/ms-marco-MiniLM-L-6-v2 for reranking
- Deployed to Streamlit Cloud and GitHub

### Key Finding: Reranking Did NOT Improve Performance
Tested on Fahrenheit 451 with 10 inference questions.

| System | Answered |
|--------|----------|
| Semantic RAG | 9/10 |
| Hybrid RAG (RRF) | 7/10 + 1 partial |
| Reranking RAG | 5/10 + 1 partial |

### Why Reranking Failed
1. First-stage recall was the bottleneck — right chunks weren't in top 20 candidates
2. Cross-encoder trained on short passages, not 500-char chunks
3. Reranking can only improve ranking quality, not recall
4. If semantic search misses the right chunk, reranking can't recover it

### Retrieval Variance Observation
- Noticed retrieved chunks differ between runs on the same question
- Live Streamlit app found an answer to Q1 that local testing missed
- Causes: embedding model randomness, cross-encoder score variance, Streamlit reruns
- Implication: single-run evaluation is not reliable
- For fair comparison, need multiple runs averaged or fixed seeds

### Code Writing Progress
- Wrote app.py with errors
- Fixed: st.cache_resource decorator, base_url formatting, deepseek_chat vs deepseek-chat, typos
- Learning through typing and fixing errors
- Still needed help with errors but understood fixes

### Resume
- Drafted with 8 projects and live URLs
- Will update with Project 9

## What I Learned

1. Reranking is not a silver bullet
2. First-stage retrieval quality determines reranking effectiveness
3. Negative results are still results — document them honestly
4. Cross-encoder model choice matters (short passages vs long chunks)
5. Retrieval has variance — same question can produce different chunks on different runs
6. Single-run evaluation is not sufficient for reliable conclusions
7. Typing code from scratch produces errors, but that's how learning happens

## Projects Now (9 total)

1. Email Generator (API wrapper)
2. Support Agent (API wrapper with RAG)
3. DocuBot (basic RAG)
4. Nimbus Coffee Fine-Tune (LoRA)
5. Semantic DocuBot (embeddings + dot product)
6. Hybrid RAG (cosine similarity + BM25 + RRF)
7. RAG Evaluation Harness (precision, recall, nDCG)
8. Nimbus Full Fine-Tune (comparison study)
9. Reranking RAG (two-stage retrieval)

## Next Steps

- Consider query expansion RAG (Project 10) to solve recall problem
- Continue concept study (12 core + 10 supporting)
- Code practice session 4 (fix empty string bug in to-do list)
- Update resume with Project 9
- Consider multi-run evaluation for more reliable results
