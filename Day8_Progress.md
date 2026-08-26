# Day 8 Progress: Concept Reinforcement + Code Practice

## What I Did Today

### Concept Quiz (12 core concepts)
- Attempted re-quiz on all 12 must-explain concepts
- NOT solid on any yet — still in learning phase
- Precision/recall: first attempt was too generic ("accuracy of positive predictions")
- No concept is interview-ready yet — all require more study
- Plan: write all 12 in physical notebook, review daily

### Physical Notebook Study
- Wrote 12 core concepts in physical notebook
- Core concepts: RAG, embeddings, fine-tuning, overfitting, gradient descent, cosine similarity, hybrid search, RRF, BM25, vector normalization, coverage vs quality, evaluation
- 10 supporting concepts listed but not yet written in notebook
- Supporting concepts: tokenization, attention, context window, hallucination, temperature, base vs fine-tuned, system vs user roles, zero-shot vs few-shot, quantization, instruction vs domain tuning

### Honest Assessment
- Yesterday struggled with gradient descent and cosine similarity
- Today still need work on ALL concepts — not just those two
- Progress is happening but slower than earlier notes suggested
- Need more repetitions before any concept is automatic

### Code Practice Session 3: To-Do List App
- Built a Streamlit to-do list app with prompts but no code shown
- Successfully wrote: session state initialization, text input, button, append logic, display
- Wrote all 8 lines from memory with only prompts for what to write next
- Identified bug: empty string can be added to list (will fix tomorrow)

### Code Practice Progress
- Session 1 (yesterday): Greeting app — needed hints for st.text_input and if statement
- Session 2 (yesterday): Counter app — needed hints for session state and st.write
- Session 3 (today): To-do list — no code shown, only prompts for what to write next

### Resume Drafted
- Created full resume with all 8 projects
- Included live URLs for every project
- Concrete metrics and findings for each project
- Placeholder for name and email (fill in later)
- Education section will evolve over time

## What I Still Need To Work On

- ALL 12 core concepts — none are interview-ready yet
- Write 10 supporting concepts in notebook
- Code from scratch without prompts
- Empty string bug in to-do list
- Resume details (name, email, LinkedIn)

## Next Project Identified

### Reranking RAG (Project 9)
- Two-stage retrieval: semantic search finds 20 candidates, cross-encoder reranks to top 10
- Uses cross-encoder/ms-marco-MiniLM-L-6-v2 for reranking
- Addresses precision weakness found in evaluation (0.125)
- Will build later today or tomorrow

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

- Write 10 supporting concepts in notebook
- Fix empty string bug in to-do list
- Build Reranking RAG project
- Daily concept review until automatic
- Resume details when ready
