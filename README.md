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

<img width="527" height="742" alt="image" src="https://github.com/user-attachments/assets/f65858eb-7465-435e-9aae-94b032c1ed2a" />


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
