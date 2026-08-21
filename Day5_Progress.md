# Day 5 Progress: Semantic RAG System

## What I built today:
- Built a complete semantic RAG system from scratch
- Learned how embeddings work for meaning-based search
- Implemented document chunking with overlap
- Used sentence-transformers to create vector embeddings
- Built vector similarity search using NumPy
- Added document summarization for abstract questions
- Solved response formatting and variation issues
- Deployed the system to the public internet

## Live Demo:
https://rag-system-420yolomcswaggerpants.streamlit.app

## GitHub Repository:
https://github.com/420yolomcswaggerpants/rag-system

## What I learned:
- Embeddings turn text into vectors that capture meaning
- Semantic search beats keyword matching for abstract questions
- Document chunking affects retrieval quality
- Summaries help with high-level questions that span the whole document
- The system prompt dramatically affects answer quality and style
- Form-based input in Streamlit allows both Enter key and button submission
- Retrieval quality is the bottleneck in RAG systems

## How It Works:
1. Document is uploaded and text extracted
2. Text is split into 500-character overlapping chunks
3. Chunks are embedded using all-MiniLM-L6-v2
4. Document summary is generated from sampled chunks
5. User question is embedded as a vector
6. Top 10 most similar chunks are retrieved
7. Summary + chunks + question are sent to DeepSeek
8. AI generates a grounded answer

## Testing Results:
Tested on Fahrenheit 451 with 10 advanced inference questions:
- 9/10 answered correctly
- Symbolism and theme questions handled well
- Character analysis questions handled well
- One question about river symbolism failed due to retrieval limitations

## Key Realizations:

### 1. RAG is a retrieval problem
The quality of answers depends on finding the right chunks. If retrieval fails, generation fails.

### 2. Embeddings capture meaning
Semantic search found relevant chunks even when keywords didn't match. That's the power of vectors.

### 3. Summaries help with abstract questions
Questions like "what is the theme" need high-level understanding, not just specific chunks.

### 4. Prompt engineering still matters
The way you structure the system prompt and user prompt dramatically affects answer quality and style.

### 5. Chunking is an art
Chunk size, overlap, and sampling strategy all affect retrieval quality.

## Tech Stack:
- Python
- Streamlit
- Sentence-Transformers
- DeepSeek API
- pypdf
- NumPy

## Next Steps:
- Add hybrid search (semantic + keyword)
- Try different embedding models
- Add evaluation metrics
- Support multiple documents
