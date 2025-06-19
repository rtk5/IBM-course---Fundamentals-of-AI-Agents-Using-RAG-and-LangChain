# 🔍 Retrieval-Augmented Generation (RAG)

Retrieval-Augmented Generation (RAG) is an AI framework designed to enhance the responses of Large Language Models (LLMs) by combining **retrieved context** with **generated natural language**.

---

## 📌 Overview

RAG optimizes LLM outputs by incorporating relevant external knowledge retrieved from a vector database. It consists of two main components:

- **Retriever**: The core of RAG, responsible for fetching relevant information.
- **Generator**: Functions as the chatbot or language model that generates the final output.

---

## ⚙️ RAG Workflow

1. **Prompt Encoding**  
   The retriever encodes the user's input (prompt) into a dense vector representation.

2. **Context Retrieval**  
   Using a vector similarity search (e.g., cosine similarity), the retriever searches the vector database to find the closest context vectors (documents or passages).

3. **Response Generation**  
   The generator (usually a transformer-based LLM) combines the retrieved context with the original prompt to generate a natural language response.

---

## 🧠 Key Components

### 1. Dense Passage Retrieval (DPR)

- **Context Encoder**  
  Encodes large chunks of text (passages or documents) into high-dimensional vectors.

- **Question Encoder**  
  Encodes the user's question into a fixed-length vector, capturing semantic meaning and context.

- **Tokenizer**  
  Both encoders use contextual tokenizers to break input into tokens and map them to embeddings.

### 2. Faiss (Facebook AI Similarity Search)

- Developed by **Facebook AI Research**, Faiss is an efficient similarity search library for large-scale, high-dimensional vector data.

- Used by the retriever to **quickly calculate distances** between the encoded question vector and the document vectors in the database.

---

## 📦 Summary

| Component        | Role                                                                 |
|------------------|----------------------------------------------------------------------|
| **Retriever**    | Encodes prompt, retrieves top-k relevant documents using Faiss       |
| **Generator**    | Combines prompt + retrieved context and generates the final output    |
| **DPR Encoders** | Encode both questions and contexts into comparable vector spaces     |
| **Faiss**        | Performs fast and accurate vector similarity search                  |

---

## 🧪 Example Use Cases

- Open-domain question answering  
- Chatbots with knowledge base grounding  
- Real-time document-based assistants
