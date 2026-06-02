# 🚀 Advanced RAG Model with Custom Knowledge Base

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![LangChain](https://img.shields.io/badge/LangChain-Enabled-green.svg)
![Gradio](https://img.shields.io/badge/Gradio-Chat%20UI-orange.svg)
![ChromaDB](https://img.shields.io/badge/ChromaDB-Vector%20Store-purple.svg)
![Groq](https://img.shields.io/badge/Groq-Fast%20Inference-black.svg)

Welcome to the **Advanced RAG (Retrieval-Augmented Generation) Model**! This project demonstrates how to build a highly efficient, conversational AI assistant that can accurately answer questions based on a custom set of documents.

By leveraging **LangChain**, **ChromaDB**, and **Groq's ultra-fast LLM API**, this system ingests raw text files, chunks them into a vector database, and uses semantic search to provide context-aware answers through a beautiful **Gradio** web interface.

---

## ✨ Features

<img width="1919" height="1079" alt="Screenshot 2026-06-02 111803" src="https://github.com/user-attachments/assets/22b6511d-c394-4e33-8531-0ccb0b19fbbd" />


- **📂 Custom Data Ingestion:** Automatically load and parse raw `.txt` and `.txt.clean` files from a designated knowledge base using a fault-tolerant loader.
- **🧠 Intelligent Text Chunking:** Splits large documents into overlapping chunks to preserve context and optimize retrieval.
- **🔍 Vector Database (Chroma):** Stores text embeddings locally using HuggingFace's `all-MiniLM-L6-v2` model for lightning-fast semantic search.
- **🔄 Smart Query Rewriting:** Automatically rewrites follow-up questions to be standalone queries, maintaining conversational context seamlessly.
- **⚡ Groq LLM Integration:** Powered by Groq's API for blazing-fast inference using advanced models like `llama-3.3-70b-versatile` or `gpt-oss-120B`.
- **💬 Interactive Chat UI:** An easy-to-use Gradio web interface to chat directly with your data.

---

## 📁 Project Structure

```text
├── knowledge-base/
│   └── text_data/            # Place all your .txt files here. This is the "brain" of the RAG.
├── vector_db/                # Auto-generated directory storing the ChromaDB SQLite database (chroma.sqlite3).
├── RAG.ipynb                 # Main Jupyter Notebook containing the end-to-end RAG pipeline.
├── .env                      # Environment variables for API keys (Groq, HuggingFace).
└── README.md                 # You are here!
```

---

## 🚀 Getting Started

### Prerequisites

Ensure you have Python 3.8+ installed. You will also need accounts with [Groq](https://console.groq.com/) and [Hugging Face](https://huggingface.co/) to generate the necessary API tokens.

### 1. Clone & Setup
Clone the repository and navigate into the project directory:
```bash
git clone https://github.com/Hardik2404/Adv_RAG.git
cd Adv_RAG
```

### 2. Install Dependencies
Install the required Python libraries using the provided `requirements.txt` file:
```bash
pip install -r requirements.txt
```

### 3. Environment Variables
Create a `.env` file in the root of your project and add your API keys:
```env
Groq_API_KEY=your_groq_api_key_here
HF_TOKEN=your_huggingface_token_here
```

### 4. Add Your Data
Drop your text files into the `knowledge-base/text_data/` folder. The system is designed to handle standard `.txt` files as well as `.txt.clean` files.

---

## 💻 Usage

1. Open the Jupyter Notebook:
```bash
jupyter notebook RAG.ipynb
```
2. **Run All Cells:** Execute the cells sequentially. The notebook will:
   - Load and authenticate your API keys.
   - Read your files from `knowledge-base/`.
   - Generate embeddings and save them to `vector_db/`.
   - Initialize the Chat UI.
3. **Chat!** At the bottom of the notebook, a local Gradio server will launch. Click the provided local URL (e.g., `http://127.0.0.1:7860/`) to open the Chat Interface and start querying your data.

---

## 🛠️ How it Works

1. **Load:** The `SafeTextLoader` reads your custom documents.
2. **Chunk:** `RecursiveCharacterTextSplitter` breaks text into 500-character chunks with 150-character overlaps.
3. **Embed:** `HuggingFaceEmbeddings` converts chunks into numerical vectors and stores them in ChromaDB.
4. **Retrieve:** When a question is asked, it's first rewritten for clarity using chat history, then used to search the vector database for the most relevant chunks.
5. **Generate:** The retrieved context is injected into a System Prompt and sent to the LLM via Groq, which returns a highly accurate, context-aware answer to the Gradio interface.

---

## 🤝 Contributing

Contributions are welcome! If you'd like to improve the data loaders, experiment with different embedding models, or enhance the UI, feel free to open a Pull Request.

## 📝 License

This project is open-source and available under the [MIT License](LICENSE).
