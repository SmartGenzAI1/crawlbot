# 🕸️ README.md 

---

ScrapAI – README.md



# ScrapAI
### AI-Powered Distributed Web Crawling, Scraping, Embedding & Semantic Search Platform

![Python](https://img.shields.io/badge/python-3.10+-blue)
![FastAPI](https://img.shields.io/badge/FastAPI-backend-green)
![Docker](https://img.shields.io/badge/docker-supported-blue)
![Status](https://img.shields.io/badge/status-development-orange)
![Architecture](https://img.shields.io/badge/architecture-distributed-purple)
![License](https://img.shields.io/badge/license-MIT-lightgrey)

---

# Overview
ScrapAI is a modular distributed system designed to crawl websites, extract content, generate embeddings, and enable semantic search over scraped data.  
The system is built with a worker-based architecture and is designed to evolve into a production-grade AI search and knowledge indexing platform.

This project is not just a scraper. It is a **content ingestion → embedding → indexing → search pipeline**.

---

# Core Features
- Distributed web crawling
- Multi-mode crawler (minimal, lightweight, full)
- Content extraction and cleaning
- Crawl queue system
- Worker-based processing
- Embedding generation pipeline
- Vector database indexing
- Semantic search foundation
- Dockerized services
- API-based architecture
- Scalable system design

---

# System Architecture

## High Level Architecture

User
                 │
                 ▼
           API Server (FastAPI)
                 │
    ┌────────────┼────────────┐
    │                           │
    ▼                           ▼

Crawl Queue                 Search API │ ▼ Crawler Worker │ ▼ Content Storage │ ▼ Embedding Worker │ ▼ Vector Database │ ▼ Semantic Search Engine

---

# Data Processing Pipeline

URL Submitted ↓ Added to Crawl Queue ↓ Crawler Worker Fetches Page ↓ HTML Parsed & Cleaned ↓ Text Content Extracted ↓ Content Stored ↓ Embedding Worker Generates Embeddings ↓ Embeddings Stored in Vector Database ↓ User Query ↓ Vector Search ↓ Relevant Documents Returned

---

# Project Structure

ScrapAI/ │ ├── backend/ │   ├── main.py │   ├── config.py │   ├── api/ │   │   └── routes.py │   ├── database/ │   │   ├── client.py │   │   ├── memory_client.py │   │   └── models.py │   └── scraper/ │       ├── crawler.py │       ├── lightweight_crawler.py │       └── minimal_crawler.py │ ├── workers/ │   ├── crawler_worker.py │   └── embedding_worker.py │ ├── docker-compose.yml ├── requirements.txt └── README.md

---

# Components

## API Server
Handles:
- Crawl requests
- Search requests
- System stats
- Page storage
- Queue management
- Worker communication

## Crawl Queue
Responsible for:
- Managing crawl tasks
- Preventing duplicate crawling
- Tracking crawl progress
- Scheduling crawl jobs

## Crawler Worker
Responsible for:
- Downloading web pages
- Parsing HTML
- Removing scripts/styles
- Extracting text content
- Generating page hash
- Sending content to storage

## Content Storage
Stores:
- URL
- Title
- Content
- Metadata
- Crawl timestamp
- Hash
- Embedding status

## Embedding Worker
Responsible for:
- Finding pages without embeddings
- Generating embeddings
- Storing vectors
- Updating embedding status

## Vector Database
Stores embeddings for:
- Semantic search
- Similarity search
- Document retrieval
- Future AI question answering

---

# System Workflow

## Crawl Workflow

User submits URL ↓ URL added to queue ↓ Crawler worker picks URL ↓ Page downloaded ↓ Content extracted ↓ Stored in database ↓ Marked for embedding

## Embedding Workflow

Embedding worker finds new pages ↓ Text converted to embeddings ↓ Embeddings stored in vector DB ↓ Page marked embedded

## Search Workflow

User query ↓ Query embedding generated ↓ Vector similarity search ↓ Top documents retrieved ↓ Results returned

---

# Running the System

## Docker (Recommended)

docker-compose up --build

## Manual Setup

pip install -r requirements.txt python backend/main.py python workers/crawler_worker.py python workers/embedding_worker.py

---

# API Endpoints

| Endpoint | Method | Description |
|---------|-------|-------------|
| /api/v1/crawl | POST | Add URL to crawl |
| /api/v1/search | GET | Search content |
| /api/v1/stats | GET | System statistics |
| /api/v1/add-page | POST | Add page manually |
| /api/v1/test-crawl | GET | Test crawler |

---

# Technology Stack

| Component | Technology |
|----------|------------|
| Backend API | FastAPI |
| Crawling | Requests / BeautifulSoup |
| Workers | Python Workers |
| Embeddings | Sentence Transformers |
| Vector DB | Chroma |
| Containerization | Docker |
| Queue | In-memory (planned Redis) |
| Database | In-memory (planned PostgreSQL) |

---

# Current Development Stage
The system is currently in **prototype / architecture stage** with the following implemented:

- Worker-based crawling
- Queue system
- Content extraction
- Embedding pipeline
- Vector storage
- API server
- Docker environment

The system architecture is designed to scale into a production-grade AI search platform.

---

# Planned Evolution
ScrapAI is intended to evolve into:

- Distributed crawler
- Semantic search engine
- AI knowledge indexing platform
- Retrieval augmented generation (RAG) system
- Autonomous web indexing engine
- AI research assistant backend
- Large-scale document retrieval system

---

# Long Term Vision Architecture

Crawler → Extract → Chunk → Embed → Vector DB → Search → AI → Answer

This architecture is used by modern AI search systems and knowledge retrieval platforms.

---

# Design Principles
- Modular architecture
- Worker-based processing
- Queue-driven pipeline
- Scalable services
- API-first design
- Containerized deployment
- Separation of concerns
- Distributed processing ready
- Vector search ready
- AI integration ready

---

# Status
Project Status: **Active Development**  
Architecture Status: **Modular Distributed System**  
Goal: **Production AI Search Platform**

---

# License
MIT License

---

# ScrapAI
Distributed AI Web Crawling and Knowledge Indexing Engine


---

