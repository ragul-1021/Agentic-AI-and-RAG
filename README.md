# Traditional RAG (Retrieval-Augmented Generation)

A Python-based Retrieval-Augmented Generation (RAG) system that retrieves relevant information from user-provided documents and uses a Large Language Model (LLM) to generate context-aware answers.

## 🚀 Features

- **Multi-format document loading** — Supports PDF, TXT, CSV, Excel, Word, and JSON files.
- **Text chunking** — Splits large documents into smaller chunks using LangChain text splitters.
- **Embedding generation** — Uses Sentence Transformers (`all-MiniLM-L6-v2`) to convert text into 384-dimensional vectors.
- **Vector storage** — Uses FAISS for efficient similarity search.
- **Semantic retrieval** — Retrieves relevant document chunks based on a user's query.
- **LLM integration** — Uses Groq-hosted language models to generate answers from retrieved context.
- **Source citations** — Displays source filenames and page information when available.
- **Query history** — Stores previous questions and answers during the current application session.
- **Optional summarization** — Generates concise summaries of answers.

## 🛠️ Tech Stack

- **Language:** Python
- **LLM integration:** LangChain and Groq
- **Embeddings:** Sentence Transformers
- **Vector database/index:** FAISS
- **Document processing:** LangChain Community Document Loaders
- **Numerical processing:** NumPy
- **Environment variables:** python-dotenv

## 📁 Project Structure

```text
traditionalRAG/
├── app.py
├── data/
├── notebook/
│   ├── data/
│   └── document.ipynb
├── src/
│   ├── data_loader.py
│   ├── embedding.py
│   ├── vectorstore.py
│   └── search.py
├── faiss_store/
├── .env
├── .gitignore
├── pyproject.toml
└── README.md
```

*The structure above is an example; adjust filenames and folders to match your actual repository.*

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/ragul-1021/Agentic-AI-and-RAG.git
cd Agentic-AI-and-RAG
```

### 2. Create and activate a virtual environment

```bash
python -m venv .venv
```

Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

### 3. Install dependencies

If your project dependencies are configured in `pyproject.toml`, install them using your preferred package manager. For example, with pip:

```bash
pip install -e .
```

### 4. Configure your Groq API key

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key
```

Load the key in Python:

```python
import os
from dotenv import load_dotenv

load_dotenv()
groq_api_key = os.getenv("GROQ_API_KEY")
```

**Security:** Never commit `.env`, API keys, or other secrets to GitHub. Add `.env` to `.gitignore`.

## 📚 Add Documents

Place your supported source documents in the data directory configured in your application. Ensure the path passed to your document loader matches the actual folder containing your files.

Supported formats include PDF, TXT, CSV, XLSX, DOCX, and JSON, subject to the corresponding loader dependencies and configuration.

## ▶️ Run the Application

From the project root, activate your virtual environment and run:

```bash
python app.py
```

The application loads documents, splits them into chunks, generates embeddings, and builds the FAISS index before retrieval and answer generation.

## 🔄 RAG Workflow

1. **Document loading:** Extract text from supported files.
2. **Text splitting:** Divide documents into manageable chunks.
3. **Embedding generation:** Convert chunks into numerical vectors.
4. **Vector indexing:** Store vectors in a FAISS index.
5. **Query embedding:** Convert the user's question into a vector.
6. **Similarity search:** Retrieve relevant chunks.
7. **Context construction:** Combine retrieved text into a prompt.
8. **Answer generation:** Send the context and question to the LLM.
9. **Response delivery:** Return the answer, available source references, and optional summary.

## 🧠 Key Concepts

- **RAG:** Combines document retrieval with LLM-based answer generation.
- **Embeddings:** Numerical representations of text used for semantic similarity.
- **Chunk size:** Controls the approximate number of characters in each text chunk.
- **Chunk overlap:** Preserves some text between adjacent chunks.
- **Top-K:** Controls the maximum number of chunks requested from retrieval.
- **Similarity threshold:** Filters retrieval results according to the score semantics implemented by the retriever.
- **Citations:** Help users locate the source documents used during retrieval.

## 🔐 Security

- Keep API keys in environment variables.
- Exclude `.env` and virtual environments from version control.
- Remove secrets from notebook outputs and Git history before publishing.
- Rotate any API key that has been exposed.
- Avoid committing private documents or sensitive user data.

## 🎯 Project Goal

The goal of this project is to build a modular RAG pipeline that can answer questions using information retrieved from user-provided documents, making document-based question answering more useful and traceable.

## 👨‍💻 Author

**Ragul B**

GitHub: [ragul-1021](https://github.com/ragul-1021)

---

*Note: Actual behavior depends on the application's implementation, configured model, available document loaders, and retrieval settings.*
