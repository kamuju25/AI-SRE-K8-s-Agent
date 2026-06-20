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

<img width="681" height="506" alt="Screenshot 2026-06-19 184703" src="https://github.com/user-attachments/assets/b10efedf-b123-402b-87c7-c45cd19520b0" />

## Workflow end-to-end

<img width="501" height="737" alt="image" src="https://github.com/user-attachments/assets/f0d9c0b7-9068-4469-95e1-f55ba3aaf441" />

## Example

<img width="492" height="456" alt="image" src="https://github.com/user-attachments/assets/3ee76f55-9b61-411b-b9b1-9bb2cf142a2b" />

Supported Kubernetes problems

  - Pending pods are detected and investigated
  - CrashLoopBackOff failures are identified and diagnosed
  - ImagePullBackOff errors are caught and analyzed
  - OOMKilled events are recognized and reported
  - Resource exhaustion is monitored and surfaced
  - Deployment rollout failures are inspected and traced
  - Service selector mismatches are discovered and flagged
  - DNS resolution problems are uncovered and examined
  - Readiness/Liveness probe failures are evaluated and explained
  - Networking issues are investigated and diagnosed
