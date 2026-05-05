# 🎓 BSNu ChatBot — AI-Powered University Assistant

A Retrieval-Augmented Generation (RAG) chatbot built for **Beni-Suef National University**, capable of answering student questions about all university faculties in both **Arabic and English**.

---

## 🚀 Features

- 🤖 AI-powered chatbot using OpenAI GPT
- 📚 Reads from 9 official faculty PDF student guides
- 🔍 Semantic search using Pinecone vector database
- 🌐 Supports Arabic and English queries
- ☁️ Google Drive integration as a dynamic knowledge base
- ⚡ Automated workflows using n8n

---

## 🏗️ Architecture

```
Google Drive (PDFs)
       ↓
  n8n Workflow
       ↓
 PDF Text Extraction
       ↓
OpenAI Embeddings
       ↓
Pinecone Vector Store
       ↓
   AI Agent (RAG)
       ↓
  Student Chat Interface
```

---

## 📁 Knowledge Base

The chatbot covers the following faculties:

| Faculty | File |
|---|---|
| Business | Business.pdf |
| Computers & AI | Computers & AI.pdf |
| Dentistry | Dentistry.pdf |
| Engineering | Engineering_Student_Guide.pdf |
| Medicine | medicine.pdf |
| Nursing | Nursing.pdf |
| Pharmacy | Pharmacy.pdf |
| Physical Therapy | Physical therapy.pdf |
| BNU General | BNU.pdf |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| [n8n](https://n8n.io) | Workflow automation |
| [OpenAI GPT-4](https://openai.com) | Language model |
| [OpenAI Embeddings](https://openai.com) | text-embedding-3-small |
| [Pinecone](https://pinecone.io) | Vector database |
| [Google Drive](https://drive.google.com) | PDF knowledge base storage |

---

## ⚙️ How It Works

### 1. Knowledge Base Pipeline
1. PDFs are uploaded to a Google Drive folder
2. Google Drive Trigger detects new files
3. Files are downloaded and parsed
4. Text is chunked and embedded using OpenAI
5. Embeddings are stored in Pinecone

### 2. RAG ChatBot Pipeline
1. Student sends a message
2. AI Agent receives the query
3. Pinecone is searched for relevant documents
4. OpenAI generates a response based on retrieved context
5. Response is returned in the same language as the query

---

## 📋 Setup

### Prerequisites
- n8n instance (self-hosted or cloud)
- OpenAI API key
- Pinecone API key
- Google Drive account

### Steps

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/bsnu-chatbot.git
```

2. **Import workflows into n8n**
   - Import `knowledge-base.json`
   - Import `rag-chatbot.json`

3. **Configure credentials in n8n**
   - Add OpenAI API key
   - Add Pinecone API key
   - Connect Google Drive account

4. **Create Pinecone index**
   - Index name: `bsnuchat`
   - Dimensions: `1536`
   - Metric: `cosine`

5. **Upload PDFs to Google Drive**
   - Create a folder named `BSNU`
   - Upload all faculty PDF guides

6. **Run the Knowledge Base workflow**
   - Trigger manually or wait for Google Drive Trigger

7. **Start chatting!**
   - Open the Chat interface in n8n

---

## 💬 Example Queries

```
ما هي كليات القطاع الطبي في جامعة بني سويف الأهلية؟
What programs are offered in the Engineering faculty?
ما هي متطلبات التسجيل في كلية الصيدلة؟
```

---

## 📄 License

MIT License — feel free to use and modify for your own university.

---

## 👤 Author

Built with ❤️ Hussein Waleed
