# Day 7 Progress: Evaluation Metrics + Code Practice

## What I Did Today

### Concept Quiz (12 must-explain concepts)
- Quized on RAG, embeddings, fine-tuning, overfitting, gradient descent, cosine similarity, hybrid search, RRF, BM25, vector normalization, coverage vs quality, evaluation
- Struggled with: gradient descent (learning rate vs weights confusion), cosine similarity (needed multiple attempts)
- Solid on: RAG, embeddings, fine-tuning, overfitting, BM25, vector normalization, coverage vs quality, evaluation

### Formal Evaluation Metrics
- Learned precision (of retrieved chunks, how many relevant?)
- Learned recall (of relevant chunks, how many retrieved?)
- Learned LLM-as-judge (use strong model to rate answer quality)
- Understood tradeoff: precision vs recall

### Project 7: RAG Evaluation Harness
- Built evaluation framework comparing semantic vs hybrid RAG
- Implemented precision and recall calculation
- Implemented LLM-as-judge with DeepSeek
- Labeled relevant chunks for 4 Fahrenheit 451 questions
- Deployed to Streamlit Cloud
- Results: Semantic RAG outperformed Hybrid on retrieval (precision 0.125 vs 0.100)

### Code Practice (from scratch)
- Built a simple Streamlit app with title, text input, button, greeting
- Struggled with: storing component values in variables, if statement colon
- Successfully wrote from memory with hints

## Key Findings

1. Quantitative evaluation contradicted manual evaluation
2. Hybrid search doesn't always beat semantic—depends on question type
3. Document summary can mask retrieval failures
4. Ground truth labeling is essential but hard

## What I Still Need To Work On

- Code from scratch (can't write without reference yet)
- Gradient descent explanation (learning rate confusion)
- Cosine similarity explanation (needed multiple attempts)
- nDCG metric (haven't learned yet)
- Full fine-tuning (not started)

## Next Steps

- More code practice
- Resume building
- Full fine-tuning
- Interview prep
