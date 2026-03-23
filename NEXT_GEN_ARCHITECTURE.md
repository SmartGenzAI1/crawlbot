 

---

# ScrapAI – Next Generation Architecture
## Goal: Perplexity-Level AI Search Engine & Autonomous Knowledge Indexing Platform

This document defines the architecture, features, and systems required to transform ScrapAI into a production-grade AI search engine comparable to modern AI search platforms.

This is not just a scraper or RAG system. The goal is to build a **full AI knowledge retrieval and reasoning engine**.

---

# Vision
ScrapAI should evolve into a system that can:
- Crawl the web
- Index knowledge
- Understand queries
- Retrieve relevant information
- Rank sources
- Generate answers
- Cite sources
- Learn from usage
- Continuously update knowledge
- Provide API access
- Scale globally

Final system type:
**Autonomous AI Search Engine**

---

# Final System Architecture

User
                     │
                     ▼
                API Gateway
                     │
    ┌────────────────┼────────────────┐
    │                │                │
    ▼                ▼                ▼

Query Service    Crawl Service    Admin Service │                │ ▼                ▼ Embedding Service   Crawl Queue │                │ ▼                ▼ Vector Search     Crawler Workers │                │ ▼                ▼ Ranking Engine     Content Extraction │                │ ▼                ▼ Context Builder     Content Storage │                │ ▼                ▼ LLM Service     Embedding Workers │                │ ▼                ▼ Answer         Vector Database

---

# Core System Layers

## 1. Crawling Layer
Responsible for collecting data from the web.

Must include:
- Distributed crawler
- Domain prioritization
- Crawl scheduling
- Recrawling
- Sitemap parsing
- Robots.txt support
- Proxy rotation
- User-agent rotation
- Crawl depth control
- Duplicate detection
- Content hashing
- Change detection

Future advanced crawling:
- Focused crawling (topic based)
- News crawling
- Research paper crawling
- Documentation crawling
- Forum crawling
- Social media crawling

---

# 2. Processing Layer
After crawling:

Pipeline:

HTML → Clean → Extract → Chunk → Metadata → Store → Embed

Metadata extraction should include:
- Title
- Author
- Publish date
- Language
- Keywords
- Entities
- Summary
- Domain authority
- Content type

---

# 3. Embedding & Indexing Layer
Must support:
- Chunk embeddings
- Page embeddings
- Metadata embeddings
- Multi-vector indexing
- Hybrid search (keyword + vector)
- Semantic clustering
- Topic indexing

Vector database options:
- Chroma
- FAISS
- Weaviate
- Milvus
- Pinecone

---

# 4. Search Layer
Search system should include:

## Types of Search
- Keyword search
- Semantic search
- Hybrid search
- Domain search
- Recent search
- Topic search
- Similar document search
- Question answering search

Search pipeline:

Query → Embedding → Vector Search → Ranking → Context → AI → Answer

---

# 5. Ranking Engine (Very Important)
This is what makes search engines powerful.

Ranking factors:
- Semantic similarity
- Keyword match
- Domain authority
- Page popularity
- Freshness
- Content length
- Content quality
- Number of sources
- Source diversity
- User clicks
- Historical performance

Ranking formula example:

Score = 0.4 Semantic Similarity + 0.2 Keyword Match + 0.15 Domain Authority + 0.15 Freshness + 0.1 Popularity

Ranking engine is required to reach Perplexity level.

---

# 6. AI / RAG Layer
This layer generates answers.

Pipeline:

User Question → Query Embedding → Vector Search → Top Documents → Context Builder → LLM → Answer → Source Citation

Advanced features:
- Multi-document reasoning
- Source citation
- Answer confidence score
- Follow-up questions
- Query rewriting
- Query expansion
- Summarization
- Comparison answers
- Timeline answers

---

# 7. Knowledge Layer (Future Advanced)
To go beyond Perplexity, add:

## Knowledge Graph
Extract:
- Entities
- People
- Companies
- Places
- Events
- Relationships

Store in graph database:
- Neo4j
- ArangoDB

This allows:
- Relationship queries
- Fact answering
- Knowledge navigation

---

# 8. Learning Layer
System should improve over time using:
- User clicks
- User queries
- Popular searches
- Failed searches
- Feedback
- Ranking adjustments

This becomes a **self-improving search engine**.

---

# Features Required to Reach Perplexity Level

## Must Have
- Distributed crawler
- Vector database
- Semantic search
- Hybrid search
- RAG answering
- Source citation
- Ranking engine
- Recrawling system
- Scheduler
- Metadata extraction
- Chunk embeddings
- Query rewriting
- Context builder
- Multi-document summarization

## Advanced
- Knowledge graph
- Personalized search
- Search history
- Query suggestions
- Topic clustering
- Trend detection
- Real-time indexing
- Research mode
- Deep search mode
- Compare mode
- Timeline mode
- Document chat
- Website chat
- API platform

---

# Infrastructure Architecture (Production)

Load Balancer
                   │
    ┌──────────────┼──────────────┐
    │              │              │
 API Server     API Server     API Server
    │
    ▼
  Redis Queue
    │

┌──────┼───────────────┐ │      │               │ Crawler Worker   Embedding Worker   Index Worker │      │               │ ▼      ▼               ▼ Proxy   GPU          Vector DB Pool    Workers │ ▼ PostgreSQL

---

# Database Architecture

## PostgreSQL
Tables:
- pages
- page_chunks
- embeddings
- crawl_queue
- domains
- users
- api_keys
- search_logs
- clicks
- rankings
- crawl_logs

## Vector DB
Stores:
- chunk embeddings
- metadata embeddings
- page embeddings

## Redis
Stores:
- queues
- cache
- sessions
- rate limits

---

# To Go Beyond Perplexity
Add unique features:

## Unique Ideas
- Website chat (chat with any website)
- Research mode (deep crawl before answering)
- Auto knowledge base builder
- Personal knowledge indexing
- Team knowledge indexing
- Private document search
- Codebase indexing
- PDF indexing
- YouTube transcript indexing
- News monitoring
- Topic tracking
- AI reports generation
- Automatic summaries of websites
- Change detection alerts
- Knowledge timeline builder
- AI agent that researches topics automatically

---

# Final Target Pipeline

Crawl → Extract → Clean → Chunk → Embed → Index → Search → Rank → Build Context → LLM → Answer → Cite Sources → Learn From Usage

This is a modern AI search engine architecture.

---

# Final Goal
ScrapAI should become:

- AI Search Engine
- Knowledge Indexing Platform
- Research Assistant Engine
- Document Search Engine
- Website Chat Engine
- Enterprise Knowledge System
- Autonomous Web Intelligence System

This is the long-term direction for the project.


---
