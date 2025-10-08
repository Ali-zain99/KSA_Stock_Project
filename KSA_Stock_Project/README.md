# 🧠 KSA Stock Portfolio Assistant

An intelligent **stock portfolio assistant** built using **Flask**, **LangChain**, **Groq LLM (LLaMA 3)**, and **Pinecone Vector Database**.  
The system provides personalized stock insights, tracks user portfolios, and enables natural language queries powered by **LLMs and embeddings**.

---

## 🚀 Features

- 🔐 **User Management:** Register and manage users with detailed personal and portfolio data.  
- 📊 **Stock Tracking:** Maintain real-time information on stock prices, sectors, and historical performance.  
- 💼 **Portfolio Management:** Track user-specific holdings, quantities, purchase prices, and fund balances.  
- 🧩 **Intelligent Querying:**  
  Uses **LangChain** with **Groq Llama3-8b** model for conversational stock-related queries.  
- 🧠 **Vector Search:**  
  Embeds user and stock data using **HuggingFace Sentence Transformers** and stores them in **Pinecone** for fast semantic retrieval.  
- ⚡ **Optimized Querying:**  
  Returns user-specific responses by retrieving and ranking context from embedded documents.  
- 🧾 **Data Integration:**  
  Joins multiple SQL tables (Users, Stocks, Portfolio, Price History, Funds) into a single, context-rich dataset.

---

## 🏗️ System Architecture

**1. Flask Backend**
- Handles user management, portfolio queries, and data joins via SQLAlchemy ORM.  
- Exports combined data to CSV for embedding and storage.

**2. Data Processing & Embedding**
- Tokenizes and filters textual data (`combined_info`).
- Generates embeddings using `sentence-transformers/all-MiniLM-L6-v2`.
- Stores embeddings in **Pinecone Vector Store** for retrieval.

**3. LLM Integration**
- Uses **LangChain** + **ChatGroq (Llama3-8b)** for natural language queries.
- Defines a **custom prompt template** for stock and portfolio questions.

**4. Context-Aware Retrieval**
- Retrieves user-specific stock and portfolio information.
- Ranks and filters documents before generating an LLM response.

---

## 🧩 Tech Stack

| Component | Technology |

|------------|-------------|

| **Backend** | Flask, SQLAlchemy |
| **Database** | MySQL |

| **LLM Interface** | LangChain, Groq (LLaMA 3) |

| **Vector Search** | Pinecone |

| **Embeddings** | HuggingFace Sentence Transformers |

| **Frontend** | Streamlit (optional for visualization) |

| **Others** | Pandas, Spacy, TensorFlow |

---

## ⚙️ Setup Instructions

### 1. Clone Repository
```bash
git clone https://github.com/yourusername/ksa-stock-assistant.git
cd ksa-stock-assistant
