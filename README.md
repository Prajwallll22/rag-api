# 🧠 RAG API with FastAPI, ChromaDB & Ollama

A Retrieval-Augmented Generation (RAG) API built with **FastAPI, ChromaDB, and Ollama**.

This project demonstrates how a RAG pipeline retrieves relevant information from a knowledge base, augments an LLM prompt with the retrieved context, and generates a grounded response.

The project was later extended to support **multiple user profiles** using ChromaDB metadata filtering.

---

## 📌 Overview

Large Language Models can generate responses using their trained knowledge, but they do not automatically have access to custom or private information.

**Retrieval-Augmented Generation (RAG)** solves this by retrieving relevant information from an external knowledge base and providing it to the language model as context.

This project implements a complete local RAG pipeline using:

- FastAPI
- ChromaDB
- Ollama
- `nomic-embed-text`
- `qwen2.5:0.5b`

The project started with a personal knowledge base and was then extended into a multi-user retrieval system.

---

## 🚀 Features

- 🔎 Semantic search
- 🧠 Retrieval-Augmented Generation
- ⚡ FastAPI REST API
- 🗃️ Persistent ChromaDB vector database
- 🤖 Local LLM inference using Ollama
- 🔢 Text embeddings using `nomic-embed-text`
- 💬 Response generation using `qwen2.5:0.5b`
- 👥 Multi-user profile support
- 🏷️ Metadata filtering
- 📄 Document/profile ingestion
- ✂️ Paragraph-based document chunking
- 🧪 Swagger UI API testing
- 💻 Fully local AI pipeline

---

## 🏗️ Architecture

```text
                        ┌──────────────┐
                        │     User     │
                        └──────┬───────┘
                               │
                               ▼
                      ┌─────────────────┐
                      │     FastAPI     │
                      │      API        │
                      └────────┬────────┘
                               │
                  ┌────────────┴────────────┐
                  │                         │
                  ▼                         ▼
           POST /documents             GET /ask
                  │                         │
                  ▼                         ▼
           Document Chunks             User Query
                  │                         │
                  ▼                         ▼
             ChromaDB              Ollama Embeddings
                  │                         │
                  │                         ▼
                  │                   Query Vector
                  │                         │
                  └────────────┬────────────┘
                               ▼
                          ChromaDB
                     Semantic Similarity
                          Search
                               │
                               ▼
                      Relevant Chunks
                               │
                               ▼
                      Augmented Prompt
                               │
                               ▼
                         Ollama LLM
                        qwen2.5:0.5b
                               │
                               ▼
                      Grounded Response
```

---

## 📡 API Endpoints

| Method | Endpoint      | Description                                      |
|--------|---------------|--------------------------------------------------|
| `POST` | `/documents`  | Ingest a user profile (chunked + embedded)       |
| `GET`  | `/ask`        | Ask a question (optional `user` filter)          |

### Example: Add a document

```bash
curl -X POST "http://localhost:8000/documents" \
  -H "Content-Type: application/json" \
  -d '{
    "user_name": "prajwal",
    "content": "My name is Prajwal Mane.\n\nI am learning cloud and AI."
  }'
```

### Example: Ask a question (all users)

```bash
curl "http://localhost:8000/ask?question=What%20is%20my%20name"
```

### Example: Ask a question (filtered by user)

```bash
curl "http://localhost:8000/ask?question=What%20is%20my%20name&user=prajwal"
```

---

## 🛠️ Setup

1. Install [Ollama](https://ollama.com/) and pull the models:

```bash
ollama pull nomic-embed-text
ollama pull qwen2.5:0.5b
```

2. Install Python dependencies (example):

```bash
pip install fastapi uvicorn chromadb ollama
```

3. (Optional) Build the initial knowledge base from `profile.txt`:

```bash
python build_knowledge_base.py
```

4. Run the API:

```bash
uvicorn main:app --reload
```

5. Open Swagger UI: [http://localhost:8000/docs](http://localhost:8000/docs)

---

## 📚 Project Documentation

A complete development walkthrough is available on NextWork:

👉 [View the full project documentation](https://nextwork.ai/enthusiastic_blue_brave_oriental_melon/docs/99ec4595-3d7b-5584-a799-aafb9c373bbb)

The documentation covers:

- Introduction to the project
- Manual RAG implementation
- Retrieval, Augmentation and Generation
- Embeddings
- Personal knowledge-base creation
- Semantic search
- FastAPI implementation
- `/ask` endpoint
- Swagger API testing
- Multi-user AI directory
- `/documents` endpoint
- ChromaDB metadata filtering
- Testing user-specific retrieval
- Project challenges and learnings

---

## 👤 Author

**Prajwal Mane** ([@Prajwallll22](https://github.com/Prajwallll22))

CSE Cybersecurity student · Cloud Security & AWS · Building with AI & DevSecOps
