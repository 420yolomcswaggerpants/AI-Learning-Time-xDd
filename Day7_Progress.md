# Day 7 Progress: Evaluation Metrics + Full Fine-Tuning

## What I Did Today

### Concept Quiz (12 must-explain concepts)
- Quizzed on: RAG, embeddings, fine-tuning, overfitting, gradient descent, cosine similarity, hybrid search, RRF, BM25, vector normalization, coverage vs quality, evaluation
- Struggled with: gradient descent (learning rate vs weights confusion), cosine similarity (needed multiple attempts)
- Solid on: RAG, embeddings, fine-tuning, overfitting, BM25, vector normalization, coverage vs quality, evaluation
- Pattern identified: absorb fast when given structure, struggle when asked to explain from scratch without framework

### Formal Evaluation Metrics
- Learned precision: of retrieved chunks, how many were relevant?
- Learned recall: of relevant chunks, how many did we retrieve?
- Learned nDCG: normalized Discounted Cumulative Gain, measures ranking quality with position awareness
- Learned LLM-as-judge: use strong model to rate answer quality
- Understood precision vs recall tradeoff

### Project 7: RAG Evaluation Harness
- Built evaluation framework comparing semantic vs hybrid RAG
- Implemented precision, recall, and nDCG calculation
- Implemented LLM-as-judge using DeepSeek
- Labeled relevant chunks for 4 Fahrenheit 451 questions
- Deployed to Streamlit Cloud
- Results: Semantic RAG outperformed Hybrid on all retrieval metrics

### Quantitative Results

| Metric | Semantic RAG | Hybrid RAG |
|--------|-------------|------------|
| Precision | 0.125 | 0.100 |
| Recall | 0.375 | 0.333 |
| nDCG | 0.343 | 0.233 |

### Key Findings
1. Quantitative evaluation contradicted manual evaluation
2. Retrieval quality and answer quality don't always correlate
3. Answer generation is noisy—same system, same question gave different answers
4. Document summary compensates for poor retrieval

### Project 8: Full Fine-Tuning
- Full fine-tuned Qwen 2.5 0.5B on 80 Q&A pairs
- Trained 25-epoch version: loss 1.861 → 0.158 in 1h 12min
- Trained 5-epoch version: loss 1.726 → 0.193 in 14min 25s
- Added weight decay 0.01 to reduce overfitting
- Deployed to HuggingFace and Streamlit Cloud

### LoRA vs Full Fine-Tuning Results

| Method | Training Questions Correct | Unseen Questions Correct |
|--------|--------------------------|-------------------------|
| LoRA | 3/4 | 0/6 |
| Full FT 25 epochs | 1.5/6 total | Poor |
| Full FT 5 epochs | 1/4 | 1/6 partially |

### Key Finding: LoRA beats Full FT on small data
- 80 examples is too small for full fine-tuning
- Full fine-tuning updates all weights and overfits quickly
- LoRA's adapter approach constrains learning, preventing overfitting
- Full fine-tuning needs 500+ examples to be effective

### Code Practice (from scratch)

**Session 1: Greeting App**
- Built Streamlit app with title, text input, button, greeting
- Struggled with: storing component values in variables, if statement colon

**Session 2: Counter App**
- Built Streamlit counter with session state
- Struggled with: displaying value vs string

### Resume Structure
- Created AI engineer resume template
- Projects as centerpiece, not education
- Need to fill in: real name, email, LinkedIn, actual URLs

## What I Learned

1. Manual evaluation is not enough—quantitative metrics reveal what casual testing misses
2. Retrieval quality and answer quality are separate things
3. LLM-as-judge is fast but has randomness
4. Small test sets limit conclusions
5. Full fine-tuning is not always better than LoRA
6. Dataset size determines which fine-tuning approach works
7. Code from scratch is possible with hints but not automatic yet

## What I Still Need To Work On

- Code from scratch without hints
- Gradient descent explanation
- Cosine similarity explanation
- Resume details (fill in real info)

## Projects Now (8 total)

1. Email Generator (API wrapper)
2. Support Agent (API wrapper with RAG)
3. DocuBot (basic RAG)
4. Nimbus Coffee Fine-Tune (LoRA)
5. Semantic DocuBot (embeddings + dot product)
6. Hybrid RAG (cosine similarity + BM25 + RRF)
7. RAG Evaluation Harness (precision, recall, nDCG)
8. Nimbus Full Fine-Tune (comparison study)

## Next Steps

- More code practice
- Resume completion
- Interview prep
- More evaluation questions
