# MCP PDF Assistant

A modular, microservice-based PDF Assistant leveraging **Machine Control Protocol (MCP)** microservices for robust PDF **extraction, chunking, embedding, vector storage**, **QnA**, and **summarization**.

Built with **modularity**, **observability**, and **extensibility** in mind. Offers both **CLI** and **Streamlit UI**. Powered by **OpenTelemetry** and **Arize Phoenix** for advanced monitoring and debugging.

---

## Table of Contents

- [Features](#features)
- [Architecture & Components](#architecture--components)
- [Workflow](#workflow)
- [Setup & Installation](#setup--installation)
- [Usage](#usage)
  - [Starting MCP Servers](#starting-mcp-servers)
  - [Streamlit UI](#streamlit-ui)
  - [Command-line Interface (CLI)](#command-line-interface-cli)
- [Environment Variables](#environment-variables)
- [Project Structure](#project-structure)
- [Extensibility & Observability](#extensibility--observability)
- [Future Enhancements](#future-enhancements)
- [License](#license)

---

## Features

- **Modular MCP microservices** for extraction, chunking, embedding, and vector storage.
- **QnA & Summarization** powered by Retrieval-Augmented Generation (RAG) + fallback LLMs.
- **Streamlit UI** for no-code operation.
- **CLI** for scripting and automation workflows.
- **Observability** via OpenTelemetry and Arize Phoenix.
- **Highly modular pipeline** for easy extension and debugging.

---

## Architecture & Components

| Component         | Responsibility                                          |
|------------------|----------------------------------------------------------|
| `extractor`      | PDF text & metadata extraction                          |
| `chunker`        | Splits content into semantic chunks                     |
| `embedder`       | Embeds chunks into vectors using LLM embeddings         |
| `vector store`   | Stores and retrieves embeddings using similarity search |
| `rag+llm`        | Handles QnA and summarization via RAG and LLM fallback  |
| `app_streamlit.py` | Streamlit-based UI                                     |
| `cli.py`         | CLI interface                                           |
| `modules/`       | Core orchestration logic                                |
| `server/`        | Hosts all microservices                                 |
| `start_mcp_servers.sh` | Script to launch all services                     |

---

## Workflow

1. **Upload PDF** → Upload document via UI or CLI.
2. **Extraction** → Extract text & metadata using `extractor`.
3. **Chunking** → Segment text into meaningful units via `chunker`.
4. **Embedding** → Convert chunks to vector embeddings using `embedder`.
5. **Vector Storage** → Save vectors into a similarity-based vector store.
6. **QnA / Summarization** → Retrieve and answer using RAG + fallback LLM.
7. **Observability** → Monitor the entire pipeline using OpenTelemetry + Phoenix.

---

## Setup & Installation

## Setup & Installation

```bash
# Clone the repo
git clone https://github.com/Hrishitcodethis/PDF-Extraction-MCP.git
cd PDF-Extraction-MCP

# Setup virtual environment
python3 -m venv .venv
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt

Be sure to set the environment variables listed below 👇

## Environment Variables

| Variable           | Description                                              |
|-------------------|----------------------------------------------------------|
| `PHOENIX_ENDPOINT`| Arize Phoenix collector endpoint                         |
| `PHOENIX_API_KEY` | *(Optional)* API key for Arize Phoenix                   |
| `OPENAI_API_KEY`  | API key for OpenAI models (embedding and generation)     |

Set these via a `.env` file, shell exports, or through your platform’s UI/environment config.

---

## Usage

### Starting MCP Servers

```bash
./start_mcp_servers.sh```

### Streamlit UI

```bash
streamlit run app_streamlit.py

### Command-line Interface (CLI)

```bash
python cli.py

## Project Structure
├── app_streamlit.py # Streamlit-based user interface
├── cli.py # CLI-based interface
├── modules/ # Pipeline orchestration logic
├── server/ # All microservices (extractor, chunker, etc.)
├── start_mcp_servers.sh # Launches all microservice servers
├── requirements.txt # Python dependencies

## Extensibility & Observability

- **Pluggable Microservices**: Easily add or swap extractors, embedders, chunkers, and vector stores to fit your specific use case.
- **Telemetry Everywhere**: Integrated with OpenTelemetry and Arize Phoenix for full pipeline observability, tracing, and performance debugging.
- **Unified Backend**: Both the Streamlit UI and CLI utilize the same modular backend, ensuring consistency across interfaces and deployment modes.

---

## Future Enhancements

- **Support for additional LLM providers** (e.g., Claude, Gemini, Mistral, local models)
- **Smarter chunking strategies** based on document layout, hierarchy, and semantics
- **Configurable pipelines** tailored for research, enterprise, and regulatory use cases
- **Multi-document summarization** (both extractive & abstractive)
- **Real-time collaboration**: Annotation, comments, and shared document review in UI
- **Cloud-ready deployments** via Docker Compose and Kubernetes
- **Extended vector DB support**: Pinecone, Weaviate, Qdrant, and more
- **Enterprise-grade security**: Role-based access, auth systems, and compliance features

---

## License

This project is licensed under the **MIT License**.  
See the [LICENSE](./LICENSE) file for more details.

---

## Why MCP PDF Assistant?

> A fast, modular, and observable PDF intelligence pipeline powered by microservices and advanced LLMs.  
> Built for researchers, developers, and enterprise teams who need reliability, flexibility, and insight-driven automation.
