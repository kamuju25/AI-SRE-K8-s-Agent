# Tech Stack

- Kubernetes cluster -> kind
- Frontend -> react
- API web framework - Python or FastAPI
- DB, Authentication, authorization, deployment, LLM integration -> InsForge
- Writing code - cursor

What is Cursor and InsForge?

Cursor and InsForge are next-generation, AI-driven software development tools that are used together to build full-stack web applications entirely through natural language prompts.

While Cursor acts as the AI-powered workspace where you type your instructions and generate the code, InsForge acts as the "agent-native" backend infrastructure that automatically spins up databases, user logins, and servers to support that code.

## Architecture

<img width="868" height="562" alt="image" src="https://github.com/user-attachments/assets/5a619106-1f59-4f7a-90ba-3e360aedd7ef" />

User → Frontend → Auth → FastAPI → (queries) → Kubernetes → (returns pod data: logs, network, deploy events, services, policies) → back to FastAPI → FastAPI sends it to LLM (InsForge/OpenRouter) → LLM summarizes → writes summary to Database (InsForge) → summary returned to User

# Prompt - To set up project

## Context

I am building a **AI K8's Troubleshooting Agent**.

Architecture:

```bash
Frontend
    ↓
FastAPI Backend (Orchestrator)
    ↓
Kubernetes Investigation Layer
    ↓
AI Kubernetes Agent
    ↓
LLM Reasoning - OpenRouter via InsForge
    ↓
Root Cause + Suggested Fix
    ↓
Frontend Diagnosis
```

This is an **on-demand troubleshooting system**.

Example flow:

```text
User clicks "Investigate Cluster"
        ↓
API call
        ↓
Kubernetes investigation
        ↓
AI reasoning
        ↓
Diagnosis shown to user
```

I am **NOT building a Kubernetes controller/operator**.

---

## Goal

Set up the project foundation.

Create:

- FastAPI backend
- Next.js frontend
- Docker setup
- Environment variables
- Basic folder structure
- Health endpoint

Do NOT implement Kubernetes logic or AI yet.

---

## Tech Stack

Backend:

- FastAPI
- Python 3.12+
- Uvicorn
- Pydantic
- Loguru
- HTTPX

Frontend:

- Next.js
- TypeScript
- Tailwind CSS
- Axios
- React Query

Infrastructure:

- Docker
- Docker Compose

---

## Project Structure

Create a monorepo:

```bash
ai-kubernetes-agent/

├── backend/
├── frontend/
├── docs/
├── prompts/
├── docker-compose.yml
└── README.md
```

Backend should include placeholders for:

```bash
api/
core/
kubernetes/
ai/
services/
models/
```

Frontend should include placeholders for:

```bash
components/
services/
hooks/
types/
```

Use placeholder implementations only.

Example:

```python
def inspect_pods():
    pass
```

---

## Backend Requirements

Create FastAPI app.

Add:

```bash
GET /health
```

Response:

```json
{
  "status": "healthy",
  "service": "ai-kubernetes-agent"
}
```

Enable:

- CORS
- logging
- env loading

Keep code simple and modular.

---

## Frontend Requirements

Create a minimal homepage.

UI:

```bash
AI Kubernetes Agent

Troubleshoot Kubernetes with AI

[ Investigate Cluster ]

System Status: Ready
```

Simple professional styling only.

---

## Environment Variables

Backend:

```env
OPENROUTER_API_KEY=
OPENROUTER_MODEL=
KUBECONFIG_PATH=
```

Frontend:

```env
NEXT_PUBLIC_API_BASE_URL=http://localhost:8000
```

---

## Docker Requirements

Create Dockerfiles for:

- backend
- frontend

Create docker-compose:

```text
backend → port 8000
frontend → port 3000
```

---

## Constraints

DO NOT implement:

- kubectl logic
- AI reasoning
- OpenRouter
- InsForge
- Authentication
- Realtime updates

Only setup the foundation.

DO NOT BREAK EXISTING CODE in future implementations.

Keep everything beginner friendly and production-style.

---

## Expected Result

I should be able to run:

```bash
docker compose up --build
```

Access:

```text
http://localhost:3000
http://localhost:8000/health
```
