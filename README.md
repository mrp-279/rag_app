# RAG App

A toy Retrieval-Augmented Generation (RAG) app: upload a PDF, it gets chunked and embedded into a local Chroma vector store, and you can then ask questions answered from that document using a local LLM via [Ollama](https://ollama.com).

## Prerequisites

- Python 3.12
- [Ollama](https://ollama.com) installed and running locally, with these models pulled:

  ```bash
  ollama pull mistral
  ollama pull nomic-embed-text
  ```

## Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
```

## Run

```bash
python app.py
```

The app serves at `http://localhost:8080`.

## Usage

- Upload a PDF via the web UI (or `POST /embed` with a `file` field) to embed it into the vector store.
- Ask a question via the web UI (or `POST /query` with JSON `{"query": "..."}`) to get an answer grounded in the uploaded document(s).

## Configuration

See `.env.example` for the available environment variables (temp upload folder, Chroma storage path, collection name, LLM model, embedding model).
