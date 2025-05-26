# Retrieval System

This directory contains the Retrieval Augmented Generation (RAG) system for Open WebUI. The RAG system enhances LLM responses by retrieving relevant information from various sources.

## Directory Structure

- `utils.py` - Utility functions for retrieval operations
- `loaders/` - Data loaders for different sources
- `models/` - Embedding and reranking models
- `vector/` - Vector database connectors
- `web/` - Web search integrations

## Core Components

### Data Loaders (`loaders/`)

Components for loading data from different sources:

- `main.py` - Main loader interface
- `mistral.py` - Mistral OCR integration
- `tavily.py` - Tavily search integration
- `youtube.py` - YouTube transcript loader

### Embedding Models (`models/`)

Models for text embedding and reranking:

- `colbert.py` - ColBERT reranking model

### Vector Database Connectors (`vector/`)

Connectors for various vector databases:

- `connector.py` - Base connector interface
- `main.py` - Main vector store interface
- `dbs/` - Database-specific implementations:
  - `chroma.py` - Chroma DB connector
  - `elasticsearch.py` - Elasticsearch connector
  - `milvus.py` - Milvus connector
  - `opensearch.py` - OpenSearch connector
  - `pgvector.py` - PostgreSQL with pgvector connector
  - `qdrant.py` - Qdrant connector

### Web Search Integrations (`web/`)

Integrations with various web search engines:

- `main.py` - Main web search interface
- `bing.py` - Bing Search integration
- `bocha.py` - Bocha Search integration
- `brave.py` - Brave Search integration
- `duckduckgo.py` - DuckDuckGo integration
- `exa.py` - Exa Search integration
- `google_pse.py` - Google Programmable Search Engine integration
- `jina_search.py` - Jina Search integration
- `kagi.py` - Kagi Search integration
- `mojeek.py` - Mojeek Search integration
- `perplexity.py` - Perplexity integration
- `searchapi.py` - SearchAPI integration
- `searxng.py` - SearXNG integration
- `serpapi.py` - SerpAPI integration
- `serper.py` - Serper integration
- `serply.py` - Serply integration
- `serpstack.py` - SerpStack integration
- `sougou.py` - Sougou Search integration
- `tavily.py` - Tavily Search integration
- `utils.py` - Web search utilities

## RAG Workflow

The RAG system follows this general workflow:

1. **Document Loading** - Documents are loaded from various sources (files, web pages, etc.)
2. **Text Chunking** - Documents are split into manageable chunks
3. **Embedding Generation** - Text chunks are converted to vector embeddings
4. **Vector Storage** - Embeddings are stored in a vector database
5. **Query Processing** - User queries are processed and converted to embeddings
6. **Retrieval** - Relevant chunks are retrieved based on semantic similarity
7. **Reranking** - Retrieved chunks are reranked for relevance (optional)
8. **Context Augmentation** - Retrieved information is added to the LLM prompt
9. **Response Generation** - The LLM generates a response using the augmented context

## Configuration Options

The RAG system can be configured through various environment variables:

- `RAG_TEMPLATE` - Template for formatting retrieved context
- `RAG_EMBEDDING_MODEL` - Model used for generating embeddings
- `RAG_RERANKING_MODEL` - Model used for reranking results
- `RAG_EMBEDDING_ENGINE` - Engine used for embeddings (OpenAI, Ollama, etc.)
- `RAG_RELEVANCE_THRESHOLD` - Minimum similarity score for inclusion
- `CHUNK_SIZE` - Size of text chunks
- `CHUNK_OVERLAP` - Overlap between adjacent chunks
- `RAG_TOP_K` - Number of chunks to retrieve
- `RAG_TOP_K_RERANKER` - Number of chunks to keep after reranking

## Vector Database Support

The RAG system supports multiple vector databases:

- **Chroma** - In-memory or persistent vector store
- **Elasticsearch** - Distributed search and analytics engine
- **Milvus** - Open-source vector database
- **OpenSearch** - Search and analytics suite
- **PostgreSQL with pgvector** - SQL database with vector extensions
- **Qdrant** - Vector search engine

## Web Search Support

The system integrates with various web search providers:

- **Bing Search**
- **Brave Search**
- **DuckDuckGo**
- **Google PSE**
- **SearXNG**
- **Serper**
- **Serply**
- **SerpStack**
- **Tavily**
- And many others

## Usage Example

Here's a simplified example of how the RAG system is used:

```python
# Load a document
document = load_document("example.pdf")

# Process and index the document
chunks = chunk_text(document.text)
embeddings = generate_embeddings(chunks)
vector_store.add(embeddings)

# Query the vector store
query = "What is the main topic?"
query_embedding = generate_embeddings(query)
results = vector_store.search(query_embedding, top_k=5)

# Generate response with context
context = format_context(results)
response = generate_llm_response(query, context)
```

## Next Steps

- [Models Documentation](../models/README.md)
- [Routers Documentation](../routers/README.md)
- [Utils Documentation](../utils/README.md)
- [Frontend Components](../../../src/lib/components/README.md)