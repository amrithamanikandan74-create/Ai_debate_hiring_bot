# AI Debate Hiring Bot

> Two AI agents debate in real-time whether to hire a candidate — powered by RAG, LangGraph, and Claude API.

## What it does

Paste any job description. Two AI agents powered by RAG:
- **Advocate** — retrieves strengths from the resume, argues why you're a great fit
- **Skeptic** — retrieves gaps vs the JD, challenges every claim
- **Judge** — reads the full debate and gives a final verdict: HIRE / MAYBE / PASS

## Tech Stack

| Layer | Tech |
|-------|------|
| Backend | FastAPI, LangGraph, ChromaDB |
| LLM | Claude API (separate system prompts per agent) |
| Frontend | React + Vite, SSE streaming |
| RAG | PyPDF2 + sentence-transformers + ChromaDB |

## Architecture

- Each agent runs independent RAG retrieval with **opposite query biases**
- Full debate history passed as context each round (multi-turn aware)
- Streamed live to the UI via Server-Sent Events (SSE)
- Shareable verdict card generated at the end

## Run locally

```bash
# Backend
cd backend
pip install -r requirements.txt
uvicorn app.main:app --reload

# Frontend
cd frontend
npm install
npm run dev
```
