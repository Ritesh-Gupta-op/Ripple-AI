# Ripple-AI

**Narrative Intelligence & Lore-Aware Storytelling Workspace**  
*Keep every detail, character, timeline, and chapter connected.*

[![React](https://img.shields.io/badge/Frontend-React%2018%20%7C%20TypeScript%20%7C%20Vite-61DAFB?logo=react&logoColor=black)](https://react.dev/)
[![FastAPI](https://img.shields.io/badge/Backend-FastAPI%20%7C%20Python%203.11+-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![RAG](https://img.shields.io/badge/RAG-Hybrid%20Dense%20%2B%20BM25%20%2B%20Graph-8b5cf6)](#-rag--narrative-architecture)
[![Gemini](https://img.shields.io/badge/LLM-Google%20Gemini%20%2F%20Claude%20%2F%20OpenAI-4285F4?logo=google&logoColor=white)](https://ai.google.dev/)
[![Demo Video](https://img.shields.io/badge/YouTube-Live%20Demo%20Video-red?logo=youtube)](https://youtu.be/E5JnvaUqCVE)

---

## 🎬 Live Demo & Video Walkthrough

Watch **Ripple AI** in action across universe tracking, scene ingestion, hybrid retrieval, and interactive CanonGraph exploration:

[![Ripple AI Demo Video](https://img.youtube.com/vi/E5JnvaUqCVE/maxresdefault.jpg)](https://youtu.be/E5JnvaUqCVE)

▶️ **[Watch the full video walkthrough on YouTube: https://youtu.be/E5JnvaUqCVE](https://youtu.be/E5JnvaUqCVE)**

---

## 📖 Overview

**Ripple AI** is an intelligent fiction writing and worldbuilding environment designed for authors, narrative designers, and screenwriters. Long-form stories span dozens of characters, factions, magical rules, relics, and converging plotlines. 

Ripple connects a sleek React-based creative workspace with a high-performance **Hybrid RAG (Retrieval-Augmented Generation) & Knowledge Graph engine**, allowing you to index raw manuscript chapters, query lore with live AI citations, audit timelines for continuity breaks, and explore dynamic relationship graphs.

---

## 🌟 Key Features

* **💬 Lore Chat (RAG Assistant):** Grounded question-answering over your manuscript. Ask about character motivations, past events, artifacts, or locations, backed by exact scene citations.
* **🛡️ Continuity Auditor:** Automated detection of timeline contradictions, character attribute mismatches, and lore inconsistencies across chapters.
* **📚 Story Universe Library:** Manage multiple fictional universes (e.g., *The Ember Archives*, *Glass Kingdom*, *Chrono Nebula*) with dedicated canon tracking.
* **📥 Scene-Aware Ingestion:** Upload `.txt` or `.md` chapters. The engine parses along natural narrative scene breaks, generates 384-dimensional dense vector embeddings, and stores them in a local SQLite database.
* **🕸️ CanonGraph Explorer:** Interactive visual graph mapping connections between characters, locations, factions, and pivotal historical events.

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    RIPPLE FRONTEND                          │
│               React 18 · TypeScript · Vite · Tailwind       │
│        (Stories · Lore Chat · Continuity · CanonGraph)      │
└──────────────────────────────┬──────────────────────────────┘
                               │ REST API (JSON / HTTP)
                               ▼
┌─────────────────────────────────────────────────────────────┐
│                   RIPPLE-RAG BACKEND                        │
│                   Python 3.10+ · FastAPI                    │
│                                                             │
│   ┌─────────────────────────┐   ┌────────────────────────┐  │
│   │       PIPELINE A        │   │       PIPELINE B       │  │
│   │   Scene-aware chunking, │   │   Hybrid retrieval:    │  │
│   │   all-MiniLM embeddings,│   │   Dense Vectors + BM25 │  │
│   │   Fact extraction       │   │   + Canon Graph Rerank │  │
│   └────────────┬────────────┘   └───────────┬────────────┘  │
└────────────────┼────────────────────────────┼───────────────┘
                 │                            │
                 ▼                            ▼
┌─────────────────────────────────────────────────────────────┐
│                     DATABASE & LLM                          │
│   SQLite (Local dev) / PostgreSQL (pgvector)                │
│   Google Gemini 3.8 / Flash · Claude · OpenAI               │
└─────────────────────────────────────────────────────────────┘
```

---

## 📁 Repository Structure

```
Ripple AI/
├── Frontend/                 # React 18 single-page application
│   ├── src/
│   │   ├── api.ts            # Axios client communicating with backend
│   │   ├── App.tsx           # Main workspace UI and page state
│   │   ├── main.tsx          # Application entrypoint
│   │   └── index.css         # Dark theme styling & animations
│   ├── package.json          # Node dependencies & Vite scripts
│   └── vite.config.ts        # Vite configuration
│
├── Backend-rag/              # Narrative RAG engine & FastAPI server
│   ├── app/
│   │   ├── api/routes/       # Endpoints: indexing, query, continuity, canon
│   │   ├── core/             # Configuration, logging, and security
│   │   ├── database/         # SQLAlchemy models and SQLite connection
│   │   ├── generation/       # LLM client (Gemini, Claude, OpenAI, Mock)
│   │   ├── pipelines/        # Ingestion and hybrid retrieval pipelines
│   │   └── main.py           # FastAPI application entrypoint
│   ├── requirements.txt      # Python dependencies
│   └── ripplerag_dev.db      # Local SQLite database (auto-generated)
│
├── Chapter_14_The_Crystal_Vault.txt  # Ready-to-use sample chapter
└── README.md                 # Project documentation
```

<img width="1903" height="811" alt="ripple frontend ss" src="https://github.com/user-attachments/assets/fe61676f-8fb8-4d33-bcf8-40fbe7e7eafd" />

## 🚀 Getting Started

### Prerequisites
Make sure you have installed:
* **Node.js** (v18.0.0 or higher) and **npm**
* **Python** (v3.10, v3.11, or v3.12)
* **Git**

---

### Step 1: Set Up the Backend (`Backend-rag`)

1. Open your terminal and navigate to the backend folder:
   ```bash
   cd "Backend-rag"
   ```

2. Create and activate a Python virtual environment:
   * **Windows (PowerShell):**
     ```powershell
     python -m venv venv
     .\venv\Scripts\Activate.ps1
     ```
   * **macOS / Linux:**
     ```bash
     python3 -m venv venv
     source venv/bin/activate
     ```

3. Install the required Python packages:
   ```bash
   pip install -r requirements.txt
   ```

4. Create your `.env` configuration:
   ```bash
   # Windows PowerShell
   Copy-Item .env.example .env

   # macOS / Linux
   cp .env.example .env
   ```

5. Configure your `.env` settings:
   ```env
   # Database (uses local SQLite out of the box)
   DATABASE_URL=sqlite:///./ripplerag_dev.db

   # Embeddings
   EMBEDDING_MODEL_NAME=sentence-transformers/all-MiniLM-L6-v2
   EMBEDDING_DIM=384

   # LLM Provider (options: gemini, openai, anthropic, mock)
   LLM_PROVIDER=gemini
   GEMINI_API_KEY=your_gemini_api_key_here
   LLM_MODEL=gemini-flash-lite-latest
   ```

6. Start the FastAPI backend server:
   ```bash
   python -m uvicorn app.main:app --reload --port 8000
   ```
   > ✅ The backend will run on `http://localhost:8000`.  
   > 📖 Interactive Swagger API Docs: `http://localhost:8000/docs`  
   > 🩺 Health Check: `http://localhost:8000/health`

---

### Step 2: Set Up the Frontend (`Frontend`)

1. Open a **second terminal tab** and navigate to the frontend folder:
   ```bash
   cd "Frontend"
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create the frontend `.env` file:
   ```env
   VITE_API_URL=http://localhost:8000
   ```

4. Start the Vite development server:
   ```bash
   npm run dev
   ```

5. Open your browser and navigate to:
   ```
   http://localhost:5173
   ```
   > Look at the bottom-right footer: you should see a green **"API connected"** indicator!

---

## 🎯 How to Use Ripple AI

### 1. Ingesting Chapters
1. In the sidebar, navigate to **Stories**.
2. Scroll to the dashed **"Import chapters or documents"** drop zone.
3. Select any `.txt` or `.md` manuscript file (or use the included `Chapter_14_The_Crystal_Vault.txt`).
4. Ripple will automatically split the chapter into scenes, calculate vector embeddings, extract canon facts, and index it into SQLite.

### 2. Asking Lore Questions (RAG)
1. In the sidebar, select **Lore Chat**.
2. Type any question about your story (e.g., *"What did Mira and Kael find in the Crystal Vault?"*).
3. The hybrid retrieval engine locates the most relevant scenes and feeds them to Gemini, generating an accurate response with chapter sources.

### 3. Running a Continuity Audit
1. In the sidebar, click **Continuity Auditor**.
2. Click **"Run new audit"**.
3. Ripple verifies consistency across indexed chapters and reports contradiction warnings or confirms that all timeline issues are clear.

### 4. Creating New Universes
1. Click the **`+`** icon in the sidebar under "YOUR STORIES" or click **"Create story"**.
2. Enter a title (e.g. *Chrono Nebula*) and description.
3. Switch universes with one click to keep multiple worlds isolated.

---

## 🔌 API Endpoints Summary

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/health` | Service health status |
| `POST` | `/api/v1/indexing/chapter` | Ingest and embed a story chapter |
| `POST` | `/api/v1/query/ask` | Query lore via hybrid RAG retrieval |
| `POST` | `/api/v1/continuity/check` | Audit chapters for narrative contradictions |
| `GET` | `/api/v1/canon/facts` | Retrieve extracted canon facts |

---

## 🛠️ Tech Stack

* **Frontend:** React 18, TypeScript, Vite, Tailwind CSS, Lucide React, Axios
* **Backend:** FastAPI, Python 3.10+, SQLAlchemy, Pydantic v2, Uvicorn
* **Embeddings & NLP:** Sentence-Transformers (`all-MiniLM-L6-v2`), Rank-BM25, NetworkX
* **Storage:** SQLite (`ripplerag_dev.db`) / PostgreSQL with `pgvector`
* **LLM Integrations:** Google Gemini (`gemini-flash-lite-latest`), Anthropic Claude, OpenAI, Ollama

---

## 📄 License

This project is licensed under the MIT License.
