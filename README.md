# Local Multimodal RAG Chatbot

A locally running **Generative AI chatbot** built using **Retrieval-Augmented Generation (RAG)** that enables users to interact with documents through context-aware conversations.

The application combines document ingestion, vector-based semantic retrieval, conversation history, and locally hosted Large Language Models (LLMs) to generate relevant, context-grounded responses.

## Overview

Traditional LLM-based chatbots rely primarily on pretrained knowledge and may not have access to specific information contained in user-provided documents.

This project addresses that limitation using Retrieval-Augmented Generation (RAG).

Documents are processed, converted into embeddings, and stored in a vector database. When a user submits a query, the system retrieves relevant document chunks and passes the retrieved context to a locally hosted LLM to generate an appropriate response.

The application also incorporates history-aware question reformulation, enabling it to understand follow-up questions using previous conversation context.

## Features

- **Document Ingestion:** Processes documents and prepares their contents for retrieval.
- **Semantic Search:** Uses vector embeddings and ChromaDB to retrieve relevant document chunks.
- **Retrieval-Augmented Generation:** Generates responses grounded in retrieved document context.
- **History-Aware Retrieval:** Reformulates follow-up questions using conversation history.
- **Prompt-Level Guardrails:** Encourages grounded responses and handles queries with insufficient supporting information.
- **Multimodal RAG:** Includes a pipeline for processing different types of content.
- **Local LLM Integration:** Uses Ollama to run language models locally.
- **Interactive Interface:** Provides a conversational interface using Streamlit.

## Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| LangChain | LLM application framework |
| Ollama | Local LLM execution |
| Llama 3.2 | Language model |
| mxbai-embed-large | Text embedding model |
| ChromaDB | Vector database |
| Streamlit | User interface |

## Architecture

```text
              USER DOCUMENTS
                    |
                    v
             DOCUMENT INGESTION
                    |
                    v
          TEXT EXTRACTION & CHUNKING
                    |
                    v
              EMBEDDING MODEL
                    |
                    v
             CHROMADB VECTOR DB
                    |
                    |
USER QUERY --------+
    |
    v
CONVERSATION HISTORY
    |
    v
HISTORY-AWARE QUERY REFORMULATION
    |
    v
          SEMANTIC RETRIEVAL
                    |
                    v
          RELEVANT DOCUMENTS
                    |
                    v
         CONTEXT + USER QUERY
                    |
                    v
               LOCAL LLM
                (OLLAMA)
                    |
                    v
          CONTEXTUAL RESPONSE
                    |
                    v
              STREAMLIT UI
```

## Project Structure

```text
GenAI-Chatbot-Local/
│
├── app.py
├── ingestion_pipeline.py
├── retrieval_pipeline.py
├── history_aware_generation.py
├── multi_modal_rag.py
├── multimodal_chat.py
├── requirements.txt
└── README.md
```

### Module Description

| File | Description |
|---|---|
| `app.py` | Streamlit application and user interface |
| `ingestion_pipeline.py` | Document ingestion and preprocessing |
| `retrieval_pipeline.py` | Retrieval of relevant document chunks |
| `history_aware_generation.py` | History-aware question reformulation and generation |
| `multi_modal_rag.py` | Multimodal RAG processing |
| `multimodal_chat.py` | Multimodal conversational pipeline |

## Getting Started

### Prerequisites

- Python 3.10 or later
- Ollama installed and running
- Git

### 1. Clone the Repository

```bash
git clone https://github.com/anushkaaaab/MultiModal-RAG-Chatbot.git

cd MultiModal-RAG-Chatbot
```

### 2. Create a Virtual Environment

```bash
python -m venv .venv
```

Activate the environment:

**Windows**

```bash
.venv\Scripts\activate
```

**Linux / macOS**

```bash
source .venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Download the Required Models

```bash
ollama pull llama3.2

ollama pull mxbai-embed-large
```

Ensure that Ollama is running before launching the application.

### 5. Run the Application

```bash
streamlit run app.py
```

Open the local URL displayed in the terminal to access the chatbot.

## How It Works

**1. Document Ingestion**

Documents are processed and divided into smaller chunks to make information retrieval more efficient.

**2. Embedding Generation**

The document chunks are converted into numerical vector representations using an embedding model.

**3. Vector Storage**

The generated embeddings are stored in ChromaDB, enabling semantic similarity-based retrieval.

**4. Query Processing**

When a user submits a question, the system considers conversation history and reformulates follow-up questions into standalone queries where necessary.

**5. Context Retrieval**

The retrieval pipeline searches the vector database for relevant document chunks.

**6. Response Generation**

The retrieved context and user query are passed to a locally hosted LLM, which generates a context-aware response.

## Learning Outcomes

- Understanding the architecture of Retrieval-Augmented Generation systems.
- Building modular LLM applications using LangChain.
- Working with vector embeddings and semantic search.
- Integrating and running open-source LLMs locally.
- Implementing conversation-aware retrieval.
- Exploring multimodal AI pipelines.
- Developing interactive AI applications using Streamlit.

## Future Improvements

- Implementing explicit user clarification for ambiguous queries.
- Improving retrieval accuracy through advanced retrieval strategies.
- Adding evaluation metrics for retrieval quality and answer relevance.
- Improving response latency and streaming.
- Strengthening guardrails through validation beyond prompt instructions.

## Author

**Anushka Bhushan**

VIT Chennai

Computer Science and Engineering | Data Science

[GitHub Profile](https://github.com/anushkaaaab)

[LinkedIn Profile](https://www.linkedin.com/in/anushka-bhushan-06b6a3293)
