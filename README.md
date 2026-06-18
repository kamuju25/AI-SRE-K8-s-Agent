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
