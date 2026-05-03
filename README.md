# PaperPilot

PaperPilot is a PDF-focused Retrieval-Augmented Generation (RAG) app that lets you upload a document and ask grounded questions over its content.

It combines chunking + embeddings + vector search + LLM answering, with Langfuse trace visibility across indexing and QA stages.

## Highlights

- Interactive PDF Q&A with source-grounded retrieval flow
- End-to-end indexing pipeline (extract -> chunk -> embed -> store)
- Qdrant vector retrieval with FAISS fallback
- Langfuse observability for latency and step-level debugging

## Tech Stack

- Python, Streamlit
- LangChain / LangGraph
- Sentence-Transformers
- Qdrant (+ FAISS fallback)
- Together AI
- Langfuse
- Docker

## Configure Secrets / Environment

Use `config/env.example` as reference and configure:

- `TOGETHER_API_KEY`
- `LANGFUSE_PUBLIC_KEY`
- `LANGFUSE_SECRET_KEY`
- `LANGFUSE_HOST` (default: `https://cloud.langfuse.com`)
- `QDRANT_URL` (default: `http://localhost:6333`)
- `QDRANT_API_KEY` (optional for local)

## Quick Start

```bash
source pdf/bin/activate
cd config && docker compose -f docker-compose.qdrant.yml up -d && cd ..
python -m streamlit run app.py
```

## Repository Guide

- Detailed setup and troubleshooting: `RUNBOOK.md`
- Core app entrypoint: `app.py`
- Pipeline modules: `backend/`

## Use Case

This project is suitable as a baseline for:

- research-paper assistants
- internal document copilots
- RAG observability and evaluation experiments
