# Agno (agno-agi)

Agno (formerly Phidata) is an open-source Python framework for building multi-agent AI systems, paired with AgentOS - a self-hostable runtime that turns agents, teams, and workflows into a REST API server with 50+ endpoints for runs, sessions, memory, knowledge, and evals. The optional os.agno.com Control Plane connects a browser directly to a self-hosted AgentOS instance for chat, tracing, and monitoring; Agno does not operate a separate multi-tenant inference API of its own.

**A note on API surface:** Agno's public HTTP API is AgentOS itself, which every user runs on their own infrastructure (default `http://localhost:7777`, or wherever it's deployed) rather than a fixed vendor-hosted base URL like a typical SaaS API. The `os.agno.com` Control Plane is a browser-based UI/monitoring layer that talks directly to your AgentOS instance from the browser - Agno's docs state "no data is sent to Agno." The core Agno Python framework (`pip install agno`) is a library, not an HTTP API, and is not modeled here as its own APIs.json entry.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/agno-agi/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/agno-agi/refs/heads/main/apis.yml)

## Tags

- AI
- Agents
- Multi-Agent
- LLM
- Framework
- Open Source
- Runtime

## Timestamps

- **Created:** 2026-07-02
- **Modified:** 2026-07-02

## APIs

### Agno AgentOS Agents API

Create, list, retrieve, and cancel runs for individual agents hosted on a self-run AgentOS instance. Runs accept a message plus optional files, session, user, and dependencies, and can return a single JSON response or stream incremental Server-Sent Events when `stream=true`.

- **Human URL:** [https://docs.agno.com/agent-os/api](https://docs.agno.com/agent-os/api)
- **Base URL:** `http://localhost:7777` (self-hosted; address depends on your deployment)

#### Tags

- Agents
- Runs
- Streaming

#### Properties

- [Documentation](https://docs.agno.com/agent-os/using-the-api)
- [API Reference](https://docs.agno.com/reference-api/schema/agents/create-agent-run)
- [OpenAPI](openapi/agno-agi-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [AsyncAPI](asyncapi/agno-agi-asyncapi.yml) — [AsyncAPI Specification](https://www.asyncapi.com/docs/reference/specification/latest)
- [Postman Collection](collections/agno-agi.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/agno-agi.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Agno AgentOS Teams API

List teams configured on an AgentOS instance and create team runs that orchestrate multiple agents against a shared task, with the same streaming, session, and file-attachment semantics as individual agent runs.

- **Human URL:** [https://docs.agno.com/agent-os/api](https://docs.agno.com/agent-os/api)
- **Base URL:** `http://localhost:7777` (self-hosted; address depends on your deployment)

#### Tags

- Teams
- Multi-Agent
- Runs

#### Properties

- [Documentation](https://docs.agno.com/agent-os/using-the-api)
- [API Reference](https://docs.agno.com/reference-api/schema/teams/list-all-teams)
- [OpenAPI](openapi/agno-agi-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/agno-agi.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/agno-agi.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Agno AgentOS Workflows API

List, execute, inspect, and cancel multi-step workflow runs over REST, with `text/event-stream` output when `stream=true`. The AgentOS Control Plane UI additionally drives workflow runs over an internal, undocumented `/workflows/ws` WebSocket that is not part of the published public API.

- **Human URL:** [https://docs.agno.com/agent-os/usage/client/run-workflows](https://docs.agno.com/agent-os/usage/client/run-workflows)
- **Base URL:** `http://localhost:7777` (self-hosted; address depends on your deployment)

#### Tags

- Workflows
- Orchestration
- Runs

#### Properties

- [Documentation](https://docs.agno.com/agent-os/usage/client/run-workflows)
- [API Reference](https://docs.agno.com/reference-api/schema/workflows/execute-workflow)
- [OpenAPI](openapi/agno-agi-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/agno-agi.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/agno-agi.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Agno AgentOS Sessions API

Create, list, retrieve, rename, and delete agent/team/workflow sessions, and list the runs that belong to a session, so conversation history and state persist across multiple requests.

- **Human URL:** [https://docs.agno.com/agent-os/api](https://docs.agno.com/agent-os/api)
- **Base URL:** `http://localhost:7777` (self-hosted; address depends on your deployment)

#### Tags

- Sessions
- Conversation History
- State

#### Properties

- [Documentation](https://docs.agno.com/agent-os/api)
- [API Reference](https://docs.agno.com/reference-api/schema/sessions/list-sessions)
- [OpenAPI](openapi/agno-agi-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### Agno AgentOS Memory API

Create, list, update, delete, and optimize persistent per-user memories, plus fetch memory topics and usage statistics, for personalizing agent behavior across sessions.

- **Human URL:** [https://docs.agno.com/agent-os/api](https://docs.agno.com/agent-os/api)
- **Base URL:** `http://localhost:7777` (self-hosted; address depends on your deployment)

#### Tags

- Memory
- Personalization
- User Memories

#### Properties

- [Documentation](https://docs.agno.com/agent-os/api)
- [API Reference](https://docs.agno.com/reference-api/schema/memory/list-memories)
- [OpenAPI](openapi/agno-agi-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### Agno AgentOS Knowledge API

Upload files, URLs, or raw text into a knowledge base with configurable chunking, then list, search, and delete indexed content that agents retrieve against at run time.

- **Human URL:** [https://docs.agno.com/agent-os/api](https://docs.agno.com/agent-os/api)
- **Base URL:** `http://localhost:7777` (self-hosted; address depends on your deployment)

#### Tags

- Knowledge
- RAG
- Vector Search

#### Properties

- [Documentation](https://docs.agno.com/agent-os/api)
- [API Reference](https://docs.agno.com/reference-api/schema/knowledge/list-content)
- [OpenAPI](openapi/agno-agi-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### Agno AgentOS Evals API

Execute accuracy, agent-as-judge, performance, and reliability evaluation runs against an agent or team, then list and update stored evaluation results to track quality over time.

- **Human URL:** [https://docs.agno.com/agent-os/api](https://docs.agno.com/agent-os/api)
- **Base URL:** `http://localhost:7777` (self-hosted; address depends on your deployment)

#### Tags

- Evals
- Evaluation
- Quality

#### Properties

- [Documentation](https://docs.agno.com/agent-os/api)
- [API Reference](https://docs.agno.com/reference-api/schema/evals/list-evaluation-runs)
- [OpenAPI](openapi/agno-agi-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

## Common Properties

- [GitHub Organization](https://github.com/agno-agi)
- [LinkedIn](https://www.linkedin.com/company/agno-agi)
- [Website](https://www.agno.com)
- [Documentation](https://docs.agno.com)
- [Plans](plans/agno-agi-plans-pricing.yml)
- [Rate Limits](rate-limits/agno-agi-rate-limits.yml)
- [Fin Ops](finops/agno-agi-finops.yml)

## Pricing Summary

- **Free** - open-source framework, local AgentOS Control Plane, chat/monitoring/knowledge/memory/evals for local use, community support.
- **Pro ($150/month)** - hosted Control Plane for a live AgentOS, 1 live connection and 4 seats included, unlimited usage/monitoring/retention/knowledge/memory/chats; add-ons at $30/month per extra seat and $95/month per extra live connection.
- **Enterprise (custom)** - everything in Pro plus dedicated Slack channel, dedicated technical lead, support SLA, custom SSO/RBAC, custom agent solutions, and a self-hosted Control Plane option.

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
