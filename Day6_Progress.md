# Day 6 Progress: Hybrid Search RAG

## What I Built

Hybrid RAG System — combines semantic search (embeddings + cosine similarity) with keyword search (BM25) using reciprocal rank fusion.

**Live:** https://hybrid-rag-420yolomcswaggerpants.streamlit.app
**GitHub:** https://github.com/420yolomcswaggerpants/hybrid-rag

## Key Concepts Learned

### Cosine Similarity vs Dot Product
- Dot product is affected by vector magnitude (longer chunks score higher)
- Cosine similarity normalizes vectors to measure angle, not magnitude
- For text embeddings, direction = meaning, so cosine is better

### BM25 Keyword Search
- Ranks chunks by exact term frequency and inverse document frequency
- Catches specific names, dates, and technical terms that semantic search might miss
- Complements semantic search because they find different things

### Reciprocal Rank Fusion (RRF)
- Weighted score fusion is sensitive to score distributions
- RRF combines ranks, not raw scores
- Formula: RRF_score = 1/(k + semantic_rank) + 1/(k + keyword_rank)
- More robust than weighted sum because ranks are scale-independent

### Hybrid Search Architecture
- Document → chunks → embeddings (semantic) + tokenized (keyword)
- Query → embedding (semantic) + tokenized (keyword)
- Two separate ranking systems
- Fused into one ranking via RRF
- Top 10 chunks sent to DeepSeek for answer generation

## Evaluation Results

Tested on Fahrenheit 451 with 10 inference questions.

| System | Answered | Notes |
|--------|----------|-------|
| Semantic RAG (dot product) | 9/10 | Best coverage, shallow answers |
| Hybrid RAG (weighted sum) | 8/10 | Deeper answers, missed inference |
| Hybrid RAG (RRF) | 7/10 + 1 partial | Deepest answers, missed symbolism |

### Key Finding
Hybrid search gives deeper analytical answers but misses abstract symbolism questions. Semantic search covers more questions but with less depth. Tradeoff between coverage and quality.

## Errors Hit and Fixed

1. **PowerShell execution policy** — tried to create venv, got security error. Decided to run globally for now.
2. **Git remote URL** — used search bar URL (no .git) instead of clone URL (with .git). Fixed by checking repo instructions.
3. **Typo in repo name** — called it "hybird-rag" on GitHub. Renamed to "hybrid-rag".
4. **Branch name mismatch** — git init defaulted to "master", push failed. Used `git branch` to check and pushed to correct branch.

## What I Understand Now

- Why cosine similarity matters for text embeddings
- How BM25 differs from semantic search
- Why rank fusion beats score fusion
- The coverage vs quality tradeoff in retrieval
- That evaluation needs to test different question types

## What I Still Don't Fully Understand

- How to tune chunk size for different document types
- When to use cross-encoders for reranking
- How to handle multi-hop questions (answer spread across chunks)
- Formal evaluation metrics (precision, recall, nDCG)

## Next Steps

- Learn formal evaluation metrics
- Full fine-tuning (not just LoRA)
- Practice explaining concepts out loud for interviews
- Build resume with 6 projects

## Projects Now

1. Email Generator (API wrapper)
2. Support Agent (API wrapper with RAG)
3. DocuBot (basic RAG)
4. Nimbus Coffee Fine-Tune (trained model)
5. Semantic DocuBot (embeddings + dot product)
6. Hybrid RAG (cosine similarity + BM25 + RRF)
