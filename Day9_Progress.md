# Day 9 Progress: Reranking RAG + Query Expansion + Code Practice

## What I Did Today

### Project 9: Reranking RAG
- Built two-stage retrieval system
- Stage 1: Semantic search finds top 20 candidates
- Stage 2: Cross-encoder reranks to top 10
- Used cross-encoder/ms-marco-MiniLM-L-6-v2 for reranking
- Deployed to Streamlit Cloud and GitHub

### Key Finding: Reranking Did NOT Improve Performance
| System | Answered |
|--------|----------|
| Semantic RAG | 9/10 |
| Hybrid RAG (RRF) | 7/10 + 1 partial |
| Reranking RAG | 5/10 + 1 partial |

### Project 10: Query Expansion RAG
- Built query expansion system using DeepSeek to generate alternative search queries
- Runs semantic search for original + 3 expanded queries
- Combines unique candidate chunks
- Deployed to Streamlit Cloud and GitHub

### Query Expansion Results
| System | Answered |
|--------|----------|
| Semantic RAG | 9/10 |
| Hybrid RAG (RRF) | 7/10 + 1 partial |
| Reranking RAG | 5/10 + 1 partial |
| Query Expansion RAG | 6/10 |

### Full System Comparison (10 questions)

| Question | Semantic | Hybrid RRF | Reranking | Query Expansion |
|----------|----------|------------|-----------|-----------------|
| Q1 Hound symbolism | Yes | No | No | No |
| Q2 Mildred TV | Yes | Yes | Partial | Yes |
| Q3 Faber vs Montag | Yes | Yes | Yes | Yes |
| Q4 Fire symbolism | Yes | No | No | No |
| Q5 Fear of books | Yes | Yes | Yes | Yes |
| Q6 Nature role | Yes | Yes | Yes | No |
| Q7 Clarisse impact | Yes | Yes | Yes | Yes |
| Q8 River symbolism | No | No | No | No |
| Q9 Hopeful ending | Yes | Yes | Yes | Yes |
| Q10 Author on tech | Yes | Yes | No | Yes |

### Major Finding: Simple Beats Complex
Semantic RAG (the simplest system) outperformed all more complex systems:
- Hybrid RAG (BM25 + RRF): worse
- Reranking RAG (cross-encoder): worse
- Query Expansion RAG (multi-query): worse

More complexity doesn't always mean better results.

### Why Complex Systems Failed
1. Symbolism questions (Q1, Q4, Q8) defeat all retrieval methods
2. Q8 fails across all systems — suggests chunking problem, not retrieval
3. Added complexity introduced noise without solving core weakness
4. Semantic search with dot product was already well-suited to this document

### Retrieval Variance Observation
- Same question can retrieve different chunks on different runs
- Live Streamlit app found an answer to Q1 that local testing missed
- Single-run evaluation is not reliable

### Code Practice Session 4: To-Do List (Fixed)
- Built to-do list with empty string check and Clear All button
- Used loop for bulleted display
- Wrote with only 2 prompts (vs many prompts yesterday)
- Added comments to code for notebook review
- Progress: needed help with almost every line → needed help with 2 things

### Code Writing Progress
- Wrote query expansion app.py with multiple errors
- Fixed: typos (endcode vs encode), missing underscores, wrong variable names
- Learning through typing and fixing errors
- Catching errors faster each time

### Resume
- Updated with 9 projects and live URLs
- Will add Project 10

## What I Learned

1. Reranking is not a silver bullet
2. Query expansion helps when vocabulary mismatch exists but hurts when original query already works
3. Simple approaches can beat complex ones
4. First-stage retrieval quality determines everything
5. Chunking strategy may be the real bottleneck for symbolism questions
6. Retrieval has variance — single-run evaluation is not reliable
7. Negative results are still results — document them honestly
8. Code writing improves with daily practice

## Projects Now (10 total)

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

## Next Steps

- Consider chunking strategy investigation (why Q8 fails everywhere)
- Continue concept study (12 core + 10 supporting)
- Code practice session 5
- Update resume with Project 10
- Consider multi-run evaluation for more reliable results
