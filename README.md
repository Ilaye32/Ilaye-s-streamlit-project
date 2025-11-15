# RAG Chatbot (LangChain + ChromaDB + AWS Deployment)

A cost‑effective **Retrieval-Augmented Generation (RAG)** chatbot built with **LangChain**, using **Hugging Face embedding models**, **ChromaDB** vector storage, and deployed on **AWS**. The system supports multiple LLMs including **Groq**, **OpenAI**, and **Gemini**, and focuses on simplicity, low cost, and modular design.

---

## ✨ Features

* **RAG Pipeline** powered by LangChain
* **Hugging Face Embeddings** for local, cost‑free embedding generation
* **ChromaDB** vector database (stored locally for affordability)
* Supports multiple LLMs:

  * **Groq** (fast & inexpensive)
  * **OpenAI** (high quality)
  * **Gemini** (Google's multimodal model)
* **LangChain Text Splitter** used for chunking documents
* Simple **HTML/CSS** frontend integration
* Deployed on **AWS EC2** for global accessibility
* No agents — **clean, controllable workflow**
* Cost‑optimized architecture using local embeddings and ChromaDB

---

## 🧠 Architecture Overview

```text
User → Frontend (HTML/CSS) → Streamlit App → LangChain Pipeline
       → Text Splitter → Embedding Model → ChromaDB → Retriever → LLM
```

---

## 🏗️ Tech Stack

**Backend:** Python, LangChain
**Embeddings:** Hugging Face (e.g. sentence-transformers)
**Vector Database:** ChromaDB (stored locally in /vectorstore folder)
**LLMs Supported:** Groq | OpenAI | Gemini
**Deployment:** AWS EC2
**Frontend:** Lightweight HTML + CSS and streamlit

---

## 📁 Project Structure

```bash
.
STREAMLIT/
│
├── code/
│   ├── app.py
│   ├── paths.py
│   ├── testing.py
│   ├── vectordb.py
│
├── publication/
│   └── publication.md
│
│
└── requirements.txt

```

---

## 🔧 Setup & Installation

### 1. Clone the repository

```bash
git clone https://github.com/Ilaye32/Ilaye-s-streamlit-project.git
cd code
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Add your API Keys

Create a `.env` file:

```env
OPENAI_API_KEY=xxxx
GROQ_API_KEY=xxxx
GEMINI_API_KEY=xxxx
```

### 4. Ingest Documents

```bash
python app.py
```

This will chunk the documents using LangChain's Text Splitter and store embeddings in **ChromaDB**.

### 5. Run the Application

```bash
python app.py
```

---

## 🚀 Deployment (AWS EC2)

* Use a **t2.micro** or **t3.micro** instance (free‑tier eligible)
* Install Python + dependencies
* Keep vectorstore on instance storage to avoid costs
* Expose port (e.g. 8501 or 80) via inbound rules
* Use Nginx or Streamlit directly

This setup is **low‑cost** because:

* Embeddings run **locally** (HuggingFace model)
* ChromaDB stores vectors **on disk**
* You only pay for the EC2 instance

---

## 🔍 How RAG Works (Simplified)

1. **User asks a question**
2. Text is passed to LangChain's Retriever
3. ChromaDB returns the most relevant chunks
4. LLM generates an answer grounded in retrieved context

---

## 📝 Example Code Snippet

```python
from langchain.text_splitter import RecursiveCharacterTextSplitter
from langchain.vectorstores import Chroma
from langchain.embeddings import HuggingFaceEmbeddings

splitter = RecursiveCharacterTextSplitter(chunk_size=800, chunk_overlap=200)
chunks = splitter.split_documents(docs)

embeddings = HuggingFaceEmbeddings(model_name="sentence-transformers/all-MiniLM-L6-v2")
vectorstore = Chroma.from_documents(chunks, embedding=embeddings, persist_directory="./vectorstore")
```

---

## 📬 Contact & Links

* **Live Demo:** *http://13.62.101.226:8501/*
* **GitHub Repo:** *https://github.com/Ilaye32/Ilaye-s-streamlit-project.git*
* **Author:** Ilaye

---

If you want, I can flesh this out further, add diagrams, or rewrite it in a more professional or more simplified tone.
