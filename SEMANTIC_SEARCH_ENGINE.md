## ScrapAI Semantic Search Engine
## No-LLM Architecture – Semantic Website Search System

This document describes the architecture, pipeline, API design, and deployment plan for ScrapAI Semantic Search Engine without using an LLM. The system will crawl websites, store content, generate embeddings, and provide semantic search via API endpoints. The main AI application can then call these endpoints.

---

# Overview
This system is a **semantic search engine**, not a chatbot.  
It retrieves relevant information from crawled websites using embeddings and vector search.

The system performs:
- Website crawling
- Content extraction
- Text chunking
- Embedding generation
- Vector indexing
- Semantic search
- Result ranking
- API search endpoint

This system can later be connected to an AI application.

---

# High Level Architecture

Internet ↓ Crawler ↓ Content Extractor ↓ SQLite Database ↓ Text Chunking ↓ Embeddings ↓ Vector Database (FAISS) ↓ Search API ↓ User / Main AI App

---

# Detailed System Architecture

User / Main AI App
                    │
                    ▼
                 FastAPI
                    │
    ┌───────────────┼───────────────┐
    │                               │
    ▼                               ▼
Search Endpoint                 Crawl Endpoint
    │                               │
    ▼                               ▼

Query Embedding                   Crawl Queue │                               │ ▼                               ▼ FAISS Search                  Crawler Worker │                               │ ▼                               ▼ Rank Results                 Extract Content │                               │ ▼                               ▼ Return Results                SQLite Database

---

# Data Processing Pipeline

## Crawling Pipeline

URL → Download HTML → Extract Text → Clean Text → Store Page

## Indexing Pipeline

Page Content → Split into Chunks → Generate Embeddings → Store in FAISS

## Search Pipeline

User Query → Query Embedding → Vector Search → Rank → Return Results

---

# Database Schema (SQLite)

## Pages Table

pages

id url title content domain created_at hash

## Chunks Table

chunks

id page_id chunk_text chunk_index

## Embeddings Table

embeddings

id chunk_id vector

## Crawl Queue Table

crawl_queue

id url status retries created_at

## Search Logs

search_logs

id query timestamp results_count

---

# API Endpoints Design

## Add URL to Crawl

POST /api/crawl

Request:

{ "url": "https://example.com" }

---

## Search Endpoint (Main Endpoint)

GET /api/search?q=your_query

Response:

{ "results": [ { "title": "...", "url": "...", "snippet": "...", "score": 0.87 } ] }

---

## Stats Endpoint

GET /api/stats

Returns:
- total pages
- total chunks
- total embeddings
- queue size

---

# How Your Main AI App Will Use This

Your main AI app will call the search endpoint:

GET https://scrapai.onrender.com/api/search?q=machine+learning

Flow:

Main AI App ↓ Call ScrapAI Search API ↓ Receive Results ↓ Use Results in AI App

So ScrapAI becomes:
## Knowledge Retrieval Backend

---

# Example Integration Flow

User asks question in AI App ↓ AI App sends query to ScrapAI ↓ ScrapAI returns relevant documents ↓ AI App uses documents ↓ AI App generates response

This is how AI systems connect to search engines.

---

# Ranking System (Simple Version)

Ranking score can be based on:

Score = 0.6 Vector Similarity + 0.2 Keyword Match + 0.1 Content Length + 0.1 Domain Score

---

# Deployment on Render Free Tier

## Yes, it can run on Render free tier if:
- Use SQLite
- Use FAISS
- Use small embedding model
- Use background worker
- Store vector index file on disk

### Render Free Tier Limits
- Service sleeps after inactivity
- Limited RAM
- Limited CPU
- Disk persists
- Good for prototype
- Not for heavy crawling

### Recommended Deployment Setup
Deploy:
- FastAPI server
- SQLite database file
- FAISS index file
- Background crawler worker

---

# Deployment Architecture (Render)

Render Web Service │ ▼ FastAPI │ ▼ SQLite DB │ ▼ FAISS Index │ ▼ Background Worker

---

# Minimum Version You Should Build First

## Version 1
- Crawl pages
- Store pages
- Chunk text
- Generate embeddings
- Store FAISS index
- Search endpoint
- Return results

## Version 2
- Ranking
- Recrawling
- Scheduler
- Domain indexing
- Metadata extraction

## Version 3
- Multi-domain crawling
- Topic search
- Similar page search
- API keys
- Logging
- Monitoring

---

# Final System Purpose

ScrapAI Semantic Search Engine will act as:
- Website search engine
- Knowledge search engine
- Backend for AI assistant
- Document retrieval system
- Research search engine
- Content indexing engine

This system can later be connected to:
- AI chatbot
- Research assistant
- Knowledge base
- Enterprise search
- Personal search engine

---

# Final Pipeline Summary

Crawl → Extract → Store → Chunk → Embed → Index → Search → Rank → Return

This is the architecture of a semantic search engine.


---

Short Answers To Your Questions

Will it work without LLM?

Yes — it becomes a semantic search engine.

Can you connect it to your main AI app later?

Yes — call /api/search endpoint.

Can it deploy on Render free tier?

Yes, if:

SQLite

FAISS

Small embedding model

Limited crawling

Background worker



---
