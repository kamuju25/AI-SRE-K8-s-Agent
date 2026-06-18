# KubeAI (K8's + AI) - troubleshooting Agent - Architecture

## Goal
AI-powered Kubernetes troubleshooting platform is to be built that enables:

- K8's failures are investigated automatically
- Logs, events, and cluster state are analyzed in real time
- Root causes are identified and surfaced to the user
- Fixes are suggested based on the identified issues
- Investigation history is stored for future reference
- The platform is deployed publicly as a real application

## High Level Design as a Visual Diagram

<img width="476" height="711" alt="image" src="https://github.com/user-attachments/assets/8b1a762e-5656-423d-81f0-8b5eacb9a6c1" />

## Workflow end-to-end

<img width="501" height="737" alt="image" src="https://github.com/user-attachments/assets/f0d9c0b7-9068-4469-95e1-f55ba3aaf441" />





```bash
You
 │
 │  "Build me a todo app with login"
 ▼
Claude Code (AI Agent)
 │
 │  understands your request
 │  writes the code
 │  runs InsForge CLI commands
 ▼
InsForge
 │
 │  receives CLI commands
 │  spins up database
 │  sets up auth
 │  deploys the app
 ▼
Your App is Live!
```
