# RAG_guided_DL

End-to-end **Retrieval-Augmented Generation (RAG)** demos in Python using **LangChain**, **SentenceTransformers**, **FAISS/Chroma**, **Groq LLMs**, **Typesense**, and **LangGraph (Agentic RAG)**.

This repo is meant as a learning playground: it walks from *raw documents → chunks → embeddings → vector store → RAG query + summarisation*, with both script-based and notebook-based workflows.

---

## Features

- 📥 **Multi-format data ingestion**
  - Load PDFs, TXT, CSV, Excel, Word, and JSON into a common document format.
- 🧩 **Chunking & embeddings**
  - Chunk documents with `RecursiveCharacterTextSplitter`.
  - Embed text using `sentence-transformers` (default: `all-MiniLM-L6-v2`).
- 📚 **Vector stores**
  - Custom **FAISS** vector store (`FaissVectorStore`) for dense retrieval.
  - Example **ChromaDB** pipeline for PDF/text in the notebooks.
- 🔍 **RAG search + summarisation**
  - Retrieve top-k relevant chunks and ask an LLM (via **Groq**) to summarise/answer.
- 🤖 **Agentic RAG with LangGraph**
  - An example LangGraph notebook for multi-step “Agentic RAG” flows.
- 🔎 **Typesense demo**
  - Build a simple search / RAG app over a books dataset using Typesense.
- 📓 **Jupyter notebooks**
  - Step-by-step notebooks for ingestion, vector DB creation, and querying.

---

## Project Structure

```text
RAG_guided_DL-main/
├── LICENSE
├── README.md                 # (this file)
├── app.py                    # Simple script wiring loader, vector store & RAG search
├── books.jsonl               # Books dataset for Typesense demo
├── data/
│   ├── pdf/
│   │   └── Deep learning.pdf
│   ├── text_files/
│   │   ├── machine_learning.txt
│   │   └── python_intro.txt
│   └── vector_store/         # Example ChromaDB store (from notebooks)
├── notebooks/
│   ├── document.ipynb        # Intro: LangChain documents & basic ingestion
│   ├── pdf_loader.ipynb      # RAG pipeline: PDF/text → ChromaDB → retrieval
│   └── pdf_loader.ipynb      # RAG pipeline: PDF/text → ChromaDB → retrieval
├── agenticrag/
│   └── 1-agenticrag.ipynb    # Agentic RAG with LangGraph
├── typesense.ipynb           # RAG / search app using Typesense + books.jsonl
└── src/
    ├── __init__.py
    ├── data_loader.py        # Load PDF/TXT/CSV/Excel/Word/JSON as LangChain docs
    ├── embedding.py          # EmbeddingPipeline: chunk + embed documents
    ├── vectorstore.py        # FaissVectorStore: build, save, load, query FAISS index
    └── search.py             # RAGSearch: retrieval + LLM summarisation over FAISS
