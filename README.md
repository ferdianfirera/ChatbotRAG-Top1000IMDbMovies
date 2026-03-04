### 🎬 RAG-Based LLM Chatbot – IMDb Top 1000 Movies

An end-to-end Retrieval-Augmented Generation (RAG) system enabling grounded, high-relevance movie question answering using vector search and reranker optimization.

![image alt](https://github.com/ferdianfirera/ChatbotRAG-Top1000IMDbMovies/blob/f0e5405bfbad5b4f02cf02b061b6e5a0a8784f2c/Screenshot%202026-03-04%20154753.png)

---


### 🧠 Problem Statement

Large Language Models generate fluent answers — but they hallucinate when lacking domain-specific context.
This project addresses that limitation by building a grounded conversational AI system using Retrieval-Augmented Generation (RAG), powered by the IMDb Top 1000 Movies dataset.
Instead of relying purely on parametric memory, the chatbot retrieves relevant documents from a vector database before generating responses — ensuring factual accuracy and contextual alignment.

---

### 🏗 System Architecture

User Query

↓

Embedding Generation

↓

Vector Similarity Search (Qdrant)

↓

Reranker Optimization

↓

Context Injection into LLM

↓

Grounded Response Generation

---

### ⚙️ Tech Stack

- Python

- LLM (OpenAI / compatible LLM)

- Qdrant Vector Database

- Custom Chunking Strategy

- Reranker for relevance optimization

- Streamlit (Interactive UI)

- Deployed via share.streamlit.io

---

### 🔍 Key Engineering Components

**1️⃣ Custom Document Ingestion Pipeline**

- Cleaned and structured IMDb Top 1000 dataset

- Designed chunking strategy to preserve semantic coherence

- Generated embeddings for each chunk

- Stored vectors in Qdrant for fast ANN search

Why this matters:
Poor chunking destroys retrieval quality. Optimized segmentation improves recall and reduces irrelevant context injection.


**2️⃣ Vector Search with Qdrant**

Qdrant enables:

- High-speed semantic retrieval

- Scalable vector storage

- Metadata filtering for contextual refinement

- The system retrieves top-K relevant chunks based on cosine similarity.


**3️⃣ Reranker Optimization**

Initial similarity search often retrieves near-relevant but suboptimal results.

To improve contextual precision:

- Applied reranking model

- Reordered candidates based on deeper semantic relevance

- Reduced noise before passing context to the LLM

This significantly improves factual grounding and response accuracy.


**4️⃣ LLM Contextual Response Generation**

The final response is generated using:

- Retrieved documents as contextual grounding

- Controlled prompt structure

- Hallucination mitigation via context injection

This ensures:

- High factual consistency

- Dataset-aligned responses

- Reduced speculative outputs

---

### 🚀 Live Demo

Streamlit interactive app deployed on:
share.streamlit.io

Users can:

Ask about movie details

Query genres, ratings, directors

Explore semantic movie insights

---

### 📂 Repository Structure

.

├── data/                    # IMDb dataset

├── ingest.py                # Data ingestion & embedding pipeline

├── Films_Database.py        # Qdrant vector database interface

├── Chat.py                  # Retrieval + LLM response generation

├── Home.py                  # Streamlit UI page

├── app.py                   # Application entry point

├── requirements.txt

└── README.md

---

### 🔄 Pipeline Explanation
**1. Data Ingestion** (`ingest.py`)

Loads IMDb dataset

Generates embeddings

Stores vectors into Qdrant collection

Run:
```bash
python ingest.py --csv data/movies.csv --collection movies
```

---

**2. Retrieval Layer (Films_Database.py)**

Handles:

- semantic similarity search

- vector queries

- context retrieval

**3. RAG Engine (Chat.py)**

- receives user query

- retrieves relevant movie chunks

- injects context into LLM prompt

- generates grounded response

**4. User Interface (Home.py, app.py)**

Interactive chatbot built with Streamlit.

Run locally:
```bash
streamlit run Home.py
```

---

### 📊 Design Decisions & Trade-Offs
**Why Qdrant?**

- Production-grade vector DB

- Faster than in-memory FAISS for scalable apps

- Supports metadata filtering

**Why Reranker?**

- Similarity search alone optimizes recall, not precision.
- Reranking increases contextual quality before generation.

**Why Streamlit?**

- Rapid prototyping

- Clean UI for recruiter demonstration

- Fast deployment

Trade-off:
Streamlit is not ideal for large-scale production APIs but effective for proof-of-concept deployment.

---

### 🧪 Future Improvements

- Hybrid search (BM25 + vector search)

- Add evaluation pipeline (RAGAS or custom grounding metrics)

- Introduce conversation memory layer

- Deploy using Docker + cloud container service

- Add monitoring for retrieval drift

---

### 🧾 What This Project Demonstrates

- End-to-end RAG system design

- Vector database integration

- Retrieval optimization via reranking

- LLM grounding techniques

- Full-stack AI deployment

This is not just a chatbot.
It is a retrieval-optimized AI system designed to minimize hallucination and maximize contextual accuracy.
