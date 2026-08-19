# Day 3 Progress: DocuBot, RAG, and the Pivot to Real AI

## What I built today:
- Completed DocuBot: a RAG app that lets users upload a PDF or text file and ask questions about it
- The AI answers based only on the document and remembers context for follow-up questions
- Added chunking, name-aware search, and document summarization
- Fixed multiple bugs including duplicate chat display, indentation errors, and retrieval failures
- Discovered the limits of naive RAG and moved to full-document inference for accuracy
- Deployed DocuBot to the public internet
- Made the strategic decision to move from API-based apps to actual model training
- Researched fine-tuning approaches and data requirements
- Identified a domain-specific text generation task for first fine-tuning project
- Set up training environment (PyTorch, Transformers, PEFT, Whisper)
- Created project structure for training pipeline
- Began data collection for fine-tuning dataset

## Live Demo:
https://docubot-420yolomcswaggerpants.streamlit.app

## GitHub Repository:
https://github.com/420yolomcswaggerpants/docubot

---

## Features:
- Upload PDF or .txt files
- Extract text from PDFs using pypdf
- Ask questions about the document
- AI answers strictly from the document
- Refuses to answer if info not present
- Remembers conversation context (follow-up questions)
- Clean chat interface with user and assistant icons
- Document preview in collapsible expander

---

## Tech Stack:
- Python
- Streamlit
- DeepSeek API
- pypdf
- Git & GitHub
- Streamlit Cloud
- PyTorch
- Hugging Face Transformers
- PEFT (LoRA)
- Whisper

---

## Skills Demonstrated:
- RAG architecture
- File upload handling
- Session state management
- Prompt engineering
- API integration
- Deployment
- Debugging Streamlit apps
- Product thinking: UX, QA, iteration
- Training environment setup
- Data collection strategy

---

## Errors Hit and Fixed:
- KeyError: DEEPSEEK_API_KEY not found (fixed by recreating .streamlit folder)
- IndentationError (fixed by properly indenting code blocks)
- NameError: user_question not defined (fixed by adding st.chat_input)
- NameError: relevant_chunks not defined (fixed by removing debug lines)
- UI rendering issues (fixed by moving history display after input processing)
- RAG retrieval failures on long documents (fixed by sending full document to AI)
- PyTorch ROCm install failure (resolved by using standard PyTorch build)

---

## Key Realizations:

### 1. Building apps that call APIs is not "AI Engineering"
I built three apps that use DeepSeek's API. That's valuable, but it's plumbing. It's not training models. It's not understanding how AI works under the hood.

### 2. RAG is harder than it looks
Simple word-matching retrieval fails on real documents. For a full novel, chunking by keywords doesn't find the right answer. Real systems use semantic search (embeddings), not Ctrl+F.

### 3. The resume needs more than apps
Apps are portfolio pieces. But to stand out, I need to show I can fine-tune a model, not just call one.

### 4. Data quality is everything
For fine-tuning, clean data matters more than volume. Pre-curated data sources reduce noise. Manual filtering is a separate skill to learn later.

### 5. Python version compatibility matters
Python 3.14 is too new for some ML libraries. GPU-accelerated PyTorch requires Python 3.12 or earlier for ROCm support. Standard PyTorch works on newer Python but runs on CPU. This tradeoff between compatibility and performance is a real consideration in AI development.

---

## What's Next:
- Finish data collection
- Format dataset for training
- Write training script using LoRA
- Run first fine-tune
- Evaluate before/after model behavior

---

## Skills Still Missing (The Real AI Work):
- Training models
- Fine-tuning
- PyTorch
- LoRA
- Evaluation metrics
- Loss curves
- Model deployment
- Dataset formatting
- Manual data filtering
