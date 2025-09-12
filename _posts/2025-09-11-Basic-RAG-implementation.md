# CleverIT RAG System

## Overview
Retrieval-Augmented Generation (RAG) system for processing Dutch-language IT documentation. Converts unstructured documents stored in structured folder system, into searchable knowledge using vector embeddings and large language models.

## Architecture

### Document Processing
- **Input formats**: PDF, TXT
- **Processing pipeline**:
  - Content extraction with PyPDF2, python-docx, textract
  - Document chunking with header context preservation
  - Metadata extraction and normalization
  - Quality assessment filtering

### AI/ML Components
- **LLM Provider**: Ollama (self-hosted)
- **Models**:
  - Gemma3:27b - document summarization
  - Llama3.2:3b - content grading
  - intfloat/multilingual-e5-large - embeddings (3840 dimensions)
- **NLP**: spaCy with Dutch language model

### Storage & Retrieval
- **Vector Database**: Qdrant with HNSW indexing
- **Search**: Semantic similarity search with relevance ranking
- **API**: FastAPI for query endpoints

### User Interface
- **Framework**: Streamlit
- **Features**:
  - User authentication
  - Query history persistence
  - Document search and exploration

## Technology Stack

| Category | Technologies |
|----------|-------------|
| **Backend** | Python 3.10+, FastAPI, asyncio/aiohttp |
| **Database** | Qdrant (vector storage), HNSW indexing |
| **AI/ML** | Ollama, Gemma3:27b, Llama3.2:3b, multilingual-e5-large |
| **Document Processing** | PyPDF2, python-docx, textract, spaCy |
| **Frontend** | Streamlit |
| **Infrastructure** | Docker, Prometheus, Sentry |
| **Data Operations** | NumPy, Faiss |

## Implementation Details

### Document Chunking Algorithm
- Preserves document structure through header context
- Maintains semantic coherence across chunks
- Configurable chunk size and overlap

### Vector Search Implementation
- HNSW index for approximate nearest neighbor search
- Cosine similarity metric
- Batch processing for multiple queries

### API Design
- RESTful endpoints for document upload and search
- Asynchronous processing for long-running tasks
- JWT-based authentication

## Performance Metrics

| Metric | Value |
|--------|-------|
| Document processing | ~500ms per page (PDF) |
| Search latency | <100ms for 10k documents |
| Embedding generation | ~200ms per chunk |
| Concurrent users | 50+ simultaneous queries |

---
*Project Period: December 2024 - March 2025*