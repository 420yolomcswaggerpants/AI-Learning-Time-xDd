# Week 1 Summary: Zero to AI Engineer Portfolio

## Overview
Six days ago, I couldn't write a line of Python. Today, I have 6 deployed AI applications, 2 fine-tuned models on HuggingFace, and a complete portfolio that demonstrates real AI engineering skills—including retrieval evaluation with documented tradeoffs.

## What Was Built

### Day 1: First Contact
- Connected to DeepSeek API
- Ran first AI-powered script
- Learned basic Python and API integration

### Day 2: First Apps
- Built and deployed AI Email Generator
- Built and deployed AI Customer Support Agent
- Learned Git, GitHub, Streamlit, and deployment

### Day 3: RAG Basics + Pivot
- Built DocuBot (basic RAG)
- Discovered API wrappers aren't AI engineering
- Decided to learn actual model training

### Day 4: Fine-Tuning
- Fine-tuned 4 models (0.5B, 1.5B, 3B)
- Learned LoRA, loss curves, training loops
- Hosted models on HuggingFace
- Deployed fine-tuned model to internet

### Day 5: Semantic RAG
- Built proper RAG with embeddings
- Implemented semantic search with dot product
- Added document summarization
- 90% accuracy on advanced inference questions

### Day 6: Hybrid Search RAG
- Built hybrid RAG combining semantic + keyword search
- Implemented cosine similarity (upgrade from dot product)
- Implemented BM25 keyword search
- Implemented reciprocal rank fusion
- Evaluated 3 systems on 10 inference questions
- Documented coverage vs quality tradeoff

## Portfolio At a Glance

| Project | Type | URL |
|---|---|---|
| Email Generator | API app | Live |
| Support Agent | API app | Live |
| DocuBot | Basic RAG | Live |
| Nimbus Fine-Tune | Trained model | Live |
| Semantic DocuBot | Real RAG | Live |
| Hybrid RAG | Hybrid search RAG | Live |

## Skills Acquired

### Programming
- Python
- Git & GitHub
- Command line
- Virtual environments (concept)

### AI Development
- API integration
- Prompt engineering
- RAG architecture
- Semantic search
- Embeddings
- Fine-tuning (LoRA)
- Training pipelines
- Cosine similarity
- BM25 keyword search
- Reciprocal rank fusion
- Retrieval evaluation

### Deployment
- Streamlit Cloud
- HuggingFace Hub
- Requirements management
- Secret management

## Key Lessons

1. **API wrappers ≠ AI engineering.** Calling an API is plumbing. Training a model is the real work.

2. **Data quality beats volume.** 80 good examples outperformed 50 mediocre ones.

3. **Loss curves tell the story.** Watching loss drop from 11.18 to 0.04 proved learning was happening.

4. **Deployment has constraints.** Free tiers can't handle large models. Smaller models deploy easier.

5. **RAG is a retrieval problem.** If you can't find the right chunks, generation fails.

6. **Embeddings capture meaning.** Semantic search found relevant info even without keyword matches.

7. **Cosine similarity beats dot product.** Normalizing vectors removes magnitude bias and measures meaning more accurately.

8. **Hybrid search is a tradeoff.** Combining semantic + keyword gives deeper answers but may miss abstract questions. Coverage vs quality is a fundamental design decision.

9. **Rank fusion beats score fusion.** Reciprocal rank fusion is robust to differences in score distributions between search methods.

10. **Evaluation must be systematic.** Testing the same questions across multiple systems reveals strengths and weaknesses you'd miss with casual testing.

## What This Proves

- Can build and deploy AI applications
- Can fine-tune open-source models
- Can implement semantic RAG systems
- Can implement hybrid search systems
- Can evaluate and compare retrieval strategies
- Can debug real-world errors
- Can document work professionally
- Can learn fast and execute

## Next Week

- Formal evaluation metrics (precision, recall, nDCG)
- Full fine-tuning (not just LoRA)
- Deeper RAG optimizations
- Interview prep and concept explanation practice
- Resume building
