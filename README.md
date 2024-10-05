# RAG Chatbot with LangChain

This project implements a Retrieval-Augmented Generation (RAG) chatbot using LangChain, with support for multiple language models including Ollama and Google's Gemini. The chatbot can process both PDF and text documents to provide context-aware responses through a Streamlit web interface.

## Features

- Support for multiple LLM backends (Ollama and Gemini)
- Document processing for both PDF and text files
- Vector storage using Chroma for efficient retrieval
- Streamlit-based chat interface
- Conversation history tracking

## Prerequisites

- Python 3.8 or higher
- Ollama (if using Ollama backend)
- Google API key (if using Gemini backend)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/rag-chatbot.git
cd rag-chatbot
```

2. Install the required dependencies:
```bash
pip install -r requirements.txt
```

3. Set up environment variables:
Create a `.env` file in the project root and add your Google API key if using Gemini:
```
GOOGLE_API_KEY=your_api_key_here
```

## Project Structure

```
.
├── RAG.py              # Main application file
├── requirements.txt    # Python dependencies
├── docs/              # Directory for storing input documents
│   ├── *.pdf         # PDF documents
│   └── *.txt         # Text documents
└── db/               # Directory for vector database storage
    └── ollama/       # Ollama-specific database files
```

## Usage

1. Place your PDF and/or text documents in the `docs/` directory.

2. Run the Streamlit application:
```bash
streamlit run RAG.py
```

3. The first run will process all documents and create the vector database. This may take some time depending on the number and size of your documents.

4. Once loaded, you can interact with the chatbot through the web interface.

## Configuration

You can switch between Ollama and Gemini models by changing the `model_type` variable in `RAG.py`:

```python
model_type = 'ollama'  # or 'gemini'
```

### Ollama Configuration
If using Ollama, ensure you have the desired model downloaded. The default model is "dolphin-mistral".

### Gemini Configuration
If using Gemini, make sure you have set up your Google API key in the `.env` file.

## How It Works

1. **Document Processing**: The application loads PDF and text documents from the `docs/` directory and splits them into manageable chunks.

2. **Embedding Generation**: Document chunks are converted into embeddings using Google's embedding model.

3. **Vector Storage**: Embeddings are stored in a Chroma vector database for efficient retrieval.

4. **Query Processing**: When a user asks a question, the application:
   - Converts the question into an embedding
   - Retrieves relevant document chunks
   - Sends the question and context to the LLM
   - Returns the generated response

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
