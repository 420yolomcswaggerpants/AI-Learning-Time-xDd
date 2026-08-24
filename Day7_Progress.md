# Day 7 Progress: Evaluation Metrics + Code Practice

## What I Did Today

### Concept Quiz (12 must-explain concepts)
- Quizzed on: RAG, embeddings, fine-tuning, overfitting, gradient descent, cosine similarity, hybrid search, RRF, BM25, vector normalization, coverage vs quality, evaluation
- Struggled with: gradient descent (learning rate vs weights confusion), cosine similarity (needed multiple attempts, pizza analogy was bad)
- Solid on: RAG, embeddings, fine-tuning, overfitting, BM25, vector normalization, coverage vs quality, evaluation
- Pattern identified: absorb fast when given structure, struggle when asked to explain from scratch without framework

### Formal Evaluation Metrics
- Learned precision: of retrieved chunks, how many were relevant?
- Learned recall: of relevant chunks, how many did we retrieve?
- Learned nDCG: normalized Discounted Cumulative Gain, measures ranking quality with position awareness
- Learned LLM-as-judge: use strong model to rate answer quality on correctness, relevance, completeness, faithfulness
- Understood precision vs recall tradeoff

### Project 7: RAG Evaluation Harness
- Built evaluation framework comparing semantic vs hybrid RAG
- Implemented precision, recall, and nDCG calculation
- Implemented LLM-as-judge using DeepSeek
- Labeled relevant chunks for 4 Fahrenheit 451 questions
- Deployed to Streamlit Cloud: https://rag-evaluation-420yolomcswaggerpants.streamlit.app
- Results: Semantic RAG outperformed Hybrid on all retrieval metrics

### Quantitative Results

| Metric | Semantic RAG | Hybrid RAG |
|--------|-------------|------------|
| Precision | 0.125 | 0.100 |
| Recall | 0.375 | 0.333 |
| nDCG | 0.343 | 0.233 |

### Key Findings
1. Quantitative evaluation contradicted manual evaluation — earlier I thought hybrid gave deeper answers, but metrics show semantic ranks better
2. Retrieval quality and answer quality don't always correlate — document summary compensates for poor retrieval on abstract questions
3. Answer generation is noisy — same system, same question gave different answers across runs
4. Ground truth labeling is hard and subjective

### Code Practice (from scratch)

**Session 1: Greeting App**
- Built Streamlit app with title, text input, button, greeting
- Struggled with: storing component values in variables, if statement colon
- Learned: f-strings, variable assignment from components

**Session 2: Counter App**
- Built Streamlit counter with session state
- Struggled with: displaying value vs string
- Learned: st.session_state persistence across reruns

### Resume Structure
- Created AI engineer resume template
- Projects as centerpiece, not education
- Need to fill in: real name, email, LinkedIn, actual URLs

## What I Learned

1. Manual evaluation is not enough — quantitative metrics reveal what casual testing misses
2. Retrieval quality and answer quality are separate things
3. LLM-as-judge is fast but has randomness
4. Small test sets limit conclusions
5. Code from scratch is possible with hints but not automatic yet

## What I Still Need To Work On

- Code from scratch without hints (can't write full app from memory yet)
- Gradient descent explanation (learning rate confusion)
- Cosine similarity explanation (needed multiple attempts)
- Full fine-tuning (not started)
- Resume details (fill in real info)

## Projects Now (7 total)

1. Email Generator (API wrapper)
2. Support Agent (API wrapper with RAG)
3. DocuBot (basic RAG)
4. Nimbus Coffee Fine-Tune (LoRA)
5. Semantic DocuBot (embeddings + dot product)
6. Hybrid RAG (cosine similarity + BM25 + RRF)
7. RAG Evaluation Harness (precision, recall, nDCG, LLM-as-judge)

## Next Steps

- Full fine-tuning (Project 8)
- More code practice
- Resume completion
- Interview prep
- More evaluation questions (4 is small sample)
