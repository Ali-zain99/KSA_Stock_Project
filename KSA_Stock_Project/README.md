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

2. Create Virtual Environment
bash
Copy code
python -m venv venv
source venv/bin/activate   # (Linux/macOS)
venv\Scripts\activate      # (Windows)
3. Install Dependencies
bash
Copy code
pip install -r requirements.txt
4. Set Up MySQL Database
Create a database named KSA_Stock_Project and update your connection string in:

python
Copy code
app.config["SQLALCHEMY_DATABASE_URI"] = 'mysql+pymysql://root:@localhost/KSA_Stock_Project'
5. Initialize Database
bash
Copy code
python
>>> from app import db
>>> db.create_all()
6. Configure API Keys
Set the following environment variables:

bash
Copy code
export GROQ_API_KEY="your_groq_api_key"
export PINECONE_API_KEY="your_pinecone_api_key"
7. Run Flask Application
bash
Copy code
python app.py
💡 Example Query
python
Copy code
user_id = 1
query = "What is my name?"
result = get_stock_info(user_id, query)
print(result)
Sample Output:

pgsql
Copy code
Your name is John Doe. You currently hold 20 shares of SABIC in the Materials sector.
📦 Data Pipeline Overview
Join Tables: User_info, Portfolio, Stocks, StockPriceHistory, Funds

Create Combined Text: Each row summarizes a user's stock, portfolio, and financial data.

Embed & Store:

Generate text embeddings.

Store in Pinecone index for vector search.

Query Processing:

Retrieve top relevant contexts.

Pass them to Groq’s LLaMA model via LangChain.

Return personalized, natural-language responses.

🧠 Example Technologies in Use
LangChain: Manages LLM interaction and retrieval pipeline.

Groq LLaMA3: Large language model for question answering.

HuggingFace Sentence Transformers: Converts structured stock data into dense embeddings.

Pinecone Vector Store: Enables similarity-based document retrieval.

Flask & SQLAlchemy: Handles backend logic and database integration.

📚 Future Enhancements
🧾 Add support for real-time stock market APIs.

💬 Integrate chat-based portfolio assistant in Streamlit UI.

🔒 Enhance authentication & authorization features.

📈 Implement visual analytics dashboards for portfolio trends.

👨‍💻 Author
Your Name
📧 your.email@example.com
🔗 LinkedIn Profile
💻 GitHub

🪪 License
This project is licensed under the MIT License — feel free to use and modify it for educational or commercial purposes.
