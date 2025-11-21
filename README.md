# 🤖 RAG Chatbot with Conversational Memory

A lightweight Retrieval-Augmented Generation (RAG) chatbot built using **LangChain**, featuring **conversational memory**, a **FastAPI backend**, and a **Streamlit UI** with document upload.

---

## ✨ Key Features

* 📄 **Upload Documents** (PDF, DOCX, HTML) — up to **200MB**
* 🧠 **Conversational Memory** — keeps context across queries
* 🤖 **Multiple LLM Options** — GPT-4o-mini & others
* 🔍 **Vector Store** — ChromaDB for efficient retrieval
* ⚡ **FastAPI Backend** — with auto-generated Swagger docs
* 📊 **LangSmith Integration** — for tracing & monitoring

---

## ⚙️ Environment Setup

Create a `.env` file in the root directory:

```env
OPENAI_API_KEY=your_openai_api_key
LANGSMITH_API_KEY=your_langsmith_api_key
```

---

## 📁 Project Layout

```
RAG-CHATBOT/
├── api/
│   ├── chroma_db/               
│   ├── chroma_utils.py          
│   ├── db_utils.py              
│   ├── langchain_utils.py       
│   ├── main.py                  
│   ├── pydantic_models.py       
│   └── rag_app.db               
├── app/
│   ├── api_utils.py             
│   ├── chat_interface.py        
│   ├── sidebar.py               
│   └── streamlit_app.py         
├── docs/                        
├── documentation/               
│   ├── screenshots/             
│   ├── api_reference.md         
│   └── user_guide.md            
├── .env                         
├── .gitignore                   
├── LICENSE                      
├── notes.txt                    
├── README.md                    
└── requirements.txt             
```

---

## 🚀 Getting Started

### 1️⃣ Installation

```bash
git clone https://github.com/YOUR-USERNAME/rag-chatbot.git
cd rag-chatbot
pip install -r requirements.txt
```

### 2️⃣ Configure Environment

```bash
cp .env.example .env
```

Add your API keys to `.env`.

### 3️⃣ Run Backend (FastAPI)

```bash
cd api
uvicorn main:app --reload --port 8000
```

### 4️⃣ Run Frontend (Streamlit)

```bash
cd app
streamlit run streamlit_app.py --server.port 8500
```

### 5️⃣ Access App

* 🖥 **Streamlit UI:** [http://localhost:8500](http://localhost:8500)
* 📘 **Swagger Docs:** [http://localhost:8000/docs](http://localhost:8000/docs)

---

## 💬 How to Use

### 📤 Upload Files

1. Open Streamlit UI
2. Upload PDFs, DOCX, or HTML
3. Files are embedded & stored in ChromaDB

### 🗣 Start Chatting

* Ask questions about your documents
* Ask **follow-up questions** — memory is maintained
* Switch LLMs anytime

---

## 🔌 API Usage (Python Example)

```python
import requests

files = {"file": open("document.pdf", "rb")}
upload_res = requests.post("http://localhost:8000/upload-doc", files=files)

chat_payload = {
    "message": "What does this document explain?",
    "session_id": "user123"
}

chat_res = requests.post("http://localhost:8000/chat", json=chat_payload)
print(chat_res.json())
```

---

## 📡 API Endpoints

| Endpoint      | Method | Purpose                          |
| ------------- | ------ | -------------------------------- |
| `/chat`       | POST   | Query with conversational memory |
| `/upload-doc` | POST   | Upload & index documents         |
| `/list-docs`  | GET    | Retrieve uploaded docs           |
| `/delete-doc` | POST   | Remove a document                |

---

## 🔧 Internal Architecture

1. **Chunking** → Document is split into text segments
2. **Embedding** → Powered by OpenAI embeddings
3. **Storage** → ChromaDB stores embeddings
4. **Retrieval** → Similar chunks fetched for each question
5. **Generation** → LLM produces answers using retrieved context
6. **Memory** → Session ID tracks conversation history

---

## 🔑 API Keys Required

| Key                            | Purpose              |
| ------------------------------ | -------------------- |
| `OPENAI_API_KEY`               | LLM & embeddings     |
| `LANGSMITH_API_KEY` (optional) | Monitoring & tracing |

---

If you want, I can also make:
✅ A more minimal version
✅ A more aesthetic emoji-heavy version
✅ A professional corporate-style README

Just tell me!
