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
