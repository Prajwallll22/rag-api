\# 🧠 RAG API with FastAPI, ChromaDB \& Ollama



A Retrieval-Augmented Generation (RAG) API built with \*\*FastAPI, ChromaDB, and Ollama\*\*.



This project demonstrates how a RAG pipeline retrieves relevant information from a knowledge base, augments an LLM prompt with the retrieved context, and generates a grounded response.



The project was later extended to support \*\*multiple user profiles\*\* using ChromaDB metadata filtering.



\---



\## 📌 Overview



Large Language Models can generate responses using their trained knowledge, but they do not automatically have access to custom or private information.



\*\*Retrieval-Augmented Generation (RAG)\*\* solves this by retrieving relevant information from an external knowledge base and providing it to the language model as context.



This project implements a complete local RAG pipeline using:



\- FastAPI

\- ChromaDB

\- Ollama

\- `nomic-embed-text`

\- `qwen2.5:0.5b`



The project started with a personal knowledge base and was then extended into a multi-user retrieval system.



\---



\# 🚀 Features



\- 🔎 Semantic search

\- 🧠 Retrieval-Augmented Generation

\- ⚡ FastAPI REST API

\- 🗃️ Persistent ChromaDB vector database

\- 🤖 Local LLM inference using Ollama

\- 🔢 Text embeddings using `nomic-embed-text`

\- 💬 Response generation using `qwen2.5:0.5b`

\- 👥 Multi-user profile support

\- 🏷️ Metadata filtering

\- 📄 Document/profile ingestion

\- ✂️ Paragraph-based document chunking

\- 🧪 Swagger UI API testing

\- 💻 Fully local AI pipeline



\---



\# 🏗️ Architecture



```text

&#x20;                        ┌──────────────┐

&#x20;                        │     User     │

&#x20;                        └──────┬───────┘

&#x20;                               │

&#x20;                               ▼

&#x20;                      ┌─────────────────┐

&#x20;                      │     FastAPI     │

&#x20;                      │      API        │

&#x20;                      └────────┬────────┘

&#x20;                               │

&#x20;                  ┌────────────┴────────────┐

&#x20;                  │                         │

&#x20;                  ▼                         ▼

&#x20;           POST /documents             GET /ask

&#x20;                  │                         │

&#x20;                  ▼                         ▼

&#x20;           Document Chunks             User Query

&#x20;                  │                         │

&#x20;                  ▼                         ▼

&#x20;             ChromaDB              Ollama Embeddings

&#x20;                  │                         │

&#x20;                  │                         ▼

&#x20;                  │                   Query Vector

&#x20;                  │                         │

&#x20;                  └────────────┬────────────┘

&#x20;                               ▼

&#x20;                          ChromaDB

&#x20;                     Semantic Similarity

&#x20;                          Search

&#x20;                               │

&#x20;                               ▼

&#x20;                      Relevant Chunks

&#x20;                               │

&#x20;                               ▼

&#x20;                      Augmented Prompt

&#x20;                               │

&#x20;                               ▼

&#x20;                         Ollama LLM

&#x20;                        qwen2.5:0.5b

&#x20;                               │

&#x20;                               ▼

&#x20;                      Grounded Response

