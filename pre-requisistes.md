Tooling


Kubernetes cluster: Kind (for spinning up a local cluster)
Frontend: React / Next.js
Backend: FastAPI (Python), using kubectl to interface with the cluster
Database, storage, authorization, LLM integration, and deployment: Insforge (an AI-native backend). Once connected to an AI coding assistant via MCP, database, storage, auth, and LLM integration can all be configured through natural-language prompts rather than manual setup — this is the main reason it's used over alternatives like Postgres or Supabase.
LLM access: OpenRouter, accessed via Insforge's Model Gateway (see below).


OpenRouter / LLM Key Setup


Why OpenRouter: Calling OpenAI or Anthropic API keys directly would be considerably more expensive. OpenRouter is multiple times cheaper, and since an Insforge account is already in use for the database, storage, and auth, it makes sense to also use Insforge's OpenRouter access rather than managing a separate provider.
Where the key comes from: The key isn't generated separately — it comes from Insforge's Model Gateway. On the Insforge dashboard, there's a "Model Gateway" section with an option to activate/start using the OpenRouter key.
How it's applied: The key is copied from the Model Gateway section and pasted into the project's .env file. Insforge also provides an example Python/FastAPI snippet showing usage — noted as functionally similar to a standard OpenAI API key, so no special handling is needed in code.
How it's invoked in the build prompts: The AI reasoning prompt explicitly instructs the coding assistant to route LLM calls through OpenRouter via the Insforge key, rather than hardcoding a direct OpenAI/Anthropic key.
Model selection note: No specific model was hardcoded, so OpenRouter automatically selects one. This affects the confidence scores returned by the agent (e.g., 75–80%) — hardcoding a stronger reasoning model would likely produce higher confidence scores.


Architecture / High-Level Design

Components:


Frontend — user connects to available Kubernetes clusters (access controlled via Insforge authorization).
FastAPI backend — uses kubectl to gather pod health/status, logs from Kubernetes resources, network inspection (latency/connectivity issues), deployment info, and Kubernetes events.
LLM reasoning layer — all collected data is sent via OpenRouter (through the Insforge API key) for root cause analysis and a suggested fix.
Insforge database — stores investigation history (rather than just returning results to the user) so past investigations can be reviewed later.


End User Workflow


User clicks "Investigate Cluster" on the frontend.
Request is authenticated/authorized.
FastAPI investigation layer collects pod status, logs, events, deployment state, and network info.
Data is sent to the LLM (via OpenRouter/Insforge) for root cause analysis and fix suggestion.
Results are saved to Insforge for investigation history, and real-time progress updates are shown to the user.

# Prerequisites:

- Docker running locally
- A local Kubernetes cluster created via Kind
- An Insforge account/project set up, with the AI coding assistant (e.g., Cursor) connected via Insforge's MCP server

# Build sequence (each done via a structured prompt to the AI coding assistant):


Project setup — scaffolds the modular folder structure (separate backend/frontend folders, Docker Compose file).
Kubernetes investigation engine — builds the FastAPI layer that acts like a "junior DevOps engineer," collecting raw evidence (pod inspector, logs collector, events analyzer, deployment inspector, kubectl executor) — no AI reasoning yet at this stage.
AI reasoning engine — adds the LLM layer that acts like a "senior Kubernetes SRE": correlates logs/events/deployment state, determines root cause, suggests fixes, and generates a confidence score.
Insforge backend integration — adds authentication (sign-up/sign-in, email verification, protected dashboard, session handling), real-time investigation progress display, investigation history, and frontend-backend integration. MCP lets the AI assistant create database tables and queries directly from documentation, rather than the developer writing SQL manually.
End-to-end integration — connects the live Kubernetes cluster(s) to the platform (e.g., pulling the cluster list from a local kubeconfig, or from SSO/another method in an organizational setting), and improves overall reliability.
