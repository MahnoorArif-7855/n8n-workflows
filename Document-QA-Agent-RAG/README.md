# 📄 Document-QA-Agent-RAG (n8n Workflow)

This project is an **n8n workflow** that implements a **Retrieval-Augmented Generation (RAG)** pipeline for answering questions about a document (e.g., a PDF stored in Google Drive).  
It integrates Google Drive, PDF parsing, vector embeddings, memory, and an AI Agent powered by OpenAI.

---

## ⚙️ Workflow Overview

### 🔹 Trigger
- **When Chat Message Received** – Starts the workflow whenever a chat message comes in.

### 🔹 Document Handling
1. **Google Drive – Download File**  
   Downloads a file (e.g., *synopsis.pdf*) from Google Drive.  
2. **Extract from File (PDF)**  
   Extracts raw text from the downloaded PDF.  
3. **Recursive Character Text Splitter**  
   Splits extracted text into manageable chunks.  
4. **Default Data Loader**  
   Loads document chunks and passes them to the vector store.  

### 🔹 Embeddings & Vector Store
5. **Embeddings OpenAI**  
   Converts document chunks into vector embeddings.  
6. **Simple Vector Store (Insert)**  
   Stores embeddings in memory for fast retrieval.  

### 🔹 AI Agent Components
7. **OpenAI Chat Model (gpt-4.1-mini)**  
   LLM used for generating answers.  
8. **Simple Vector Store (Retrieve as Tool)**  
   Provides document-grounded context to the agent when a user asks a question.  
9. **Simple Memory (Buffer)**  
   Maintains conversation history for multi-turn interactions.  
10. **AI Agent**  
   Orchestrates the LLM, memory, and vector store tools to provide contextual answers.  

---

## ✅ Example Flow

**User query:**  
```
What is the main contribution of this synopsis?
```

**Workflow execution:**  
1. Downloads & extracts text from the PDF.  
2. Splits text and generates embeddings.  
3. Stores them in the in-memory vector store.  
4. Retrieves relevant chunks when queried.  
5. OpenAI model generates an answer grounded in the retrieved content.  

**Agent response:**  
```
The synopsis focuses on a multi-step reasoning approach for improving explanation generation in Visual Question Answering (VQA).
```

---

## 📂 Folder Structure

```
Document-QA-Agent-RAG/
│── RAG AI Agent.json      # Exported n8n workflow
│── README.md              # Project documentation
```

---

## 🚀 Usage

1. Import `RAG AI Agent.json` into **n8n** (`Workflows → Import from File`).  
2. Configure credentials:  
   - Google Drive OAuth2 API  
   - OpenAI API key  
3. Run the workflow or connect it to your chat interface.  
4. Ask questions about the uploaded document.  

---

## 📝 Notes
- Document source: **Google Drive** (can be replaced with other sources).  
- Embeddings + LLM both use **OpenAI**.  
- Uses **in-memory vector store** (suitable for demos; switch to Pinecone/Weaviate for production).  
- Memory buffer ensures conversational context.  

---

## 🔮 Future Enhancements
- Add support for multiple document uploads.  
- Connect to external vector DB (Pinecone, FAISS, Weaviate).  
- Extend to support summarization of multiple docs.  
