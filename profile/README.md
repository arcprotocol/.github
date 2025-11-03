# ARC Ecosystem - Agent Communication Infrastructure

# <img src="../assets/arc_banner.jpeg" alt="ARC Protocol" width="100%">

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![GitHub stars](https://img.shields.io/github/stars/arcprotocol/arcprotocol.svg?style=social&label=Star)](https://github.com/arcprotocol/arcprotocol)
[![Discord](https://img.shields.io/discord/1234567890?color=7289da&label=Discord&logo=discord)](https://discord.gg/XYmp22xX5m)
[![Twitter Follow](https://img.shields.io/twitter/follow/arcprotocol?style=social)](https://twitter.com/arcprotocol)

## TOP Level Families

<img src="../assets/arc-family.png" alt="ARC Top Level Families" width="100%">

The ARC Ecosystem provides an infrastructure for agent-to-agent communication, discovery, and routing through three top-level families:

- **ARC Protocol** - The communication layer for agent interactions
- **ARC Compass** - The agent search engine for finding the right agents
- **ARC Ledger** - The centralized registry for agent capabilities

## ARC Protocol

**ARC Protocol** is a communication standard between agents for multi-agent systems. The protocol enables hosting multiple agent types on a single endpoint with agent-level routing via `requestAgent` and `targetAgent` fields, and provides workflow tracing capabilities designed for integration with monitoring platforms.

### Key Features

- **Multi-Agent Architecture**: Single endpoint supports multiple agents with agent identification at protocol level
- **Agent-Centric Routing**: Identify request source and target at protocol level with `requestAgent`/`targetAgent` fields
- **Workflow Tracing**: End-to-end traceability across multi-agent processes via `traceId`
- **Stateless Design**: Each request is independent with no session state
- **Method-Based**: Clean RPC-style method invocation
- **HTTPS Transport**: Works over HTTPS with POST requests
- **Server-Sent Events**: Support for streaming responses via SSE

```python
# Create a new task
task = await client.task_create(
    request_agent="user-interface-01",
    target_agent="document-analyzer-01",
    initial_message={"role": "user", "parts": [{"type": "TextPart", "content": "Analyze quarterly report"}]}
)

# Check progress
status = await client.task_info(
    request_agent="user-interface-01",
    target_agent="document-analyzer-01",
    task_id=task.task.taskId
)
```

## ARC Ledger

**ARC Ledger** is a centralized agent discovery registry that maintains information about available agents, their capabilities, and endpoints. When integrated with ARC Protocol, it provides a structured approach to agent discovery and communication.

### Key Features

- **Agent Registration**: Agents register their capabilities and endpoints
- **Agent Discovery**: Applications query for agents based on required capabilities
- **Metadata Management**: Store and retrieve agent metadata
- **Dynamic Updates**: Agents can update their status and capabilities as they evolve

## ARC Compass

**ARC Compass** is an agent search engine with ranking algorithms for finding optimal agents. It queries ARC Ledger and returns ranked agent recommendations based on capability matching.

### Key Features

- **Agent Search**: Find agents based on capabilities and requirements
- **Ranking Algorithm**: Evaluate and rank agents based on suitability for specific tasks
- **Dynamic Discovery**: Automatically adapt to new or updated agents in ARC Ledger
- **Capability Matching**: Match task requirements with agent capabilities

## How It All Works Together

The ARC Ecosystem components work together to provide agent discovery, selection, and communication:

1. **Agent Registration**: Agents register their capabilities with ARC Ledger
2. **Agent Discovery**: Applications query ARC Compass to find appropriate agents
3. **Agent Selection**: ARC Compass uses its ranking algorithms to search through ARC Ledger
4. **Agent Communication**: Applications use ARC Protocol to communicate with selected agents

```
Agent/Supervisor → ARC Compass → ARC Ledger → Target Agent (via ARC Protocol)
```

## SDK Implementations

Currently available SDK:

- [**Python SDK**](https://github.com/arcprotocol/python-sdk) - Reference implementation

## Comparison to Existing Protocols

### Agent Protocol Comparison

| Feature | ARC | ACP (Agent Communication Protocol) | A2A (Agent-to-Agent) |
|---------|-----|-----------------------------------|----------------------|
| **Primary Purpose** | Agent communication standard | Agent lifecycle management | Agent interoperability |
| **Agent Identification** | `requestAgent`/`targetAgent` fields | Agent URI | Agent Cards |
| **Workflow Tracing** | `traceId` for monitoring integration | Built-in tracing | Task tracking |
| **Message Format** | JSON-based | REST/MIME-based | JSON-based |
| **Transport** | HTTPS | REST/HTTP | HTTP/SSE |
| **Real-time Support** | SSE streaming | Streaming | SSE/Webhook |
| **Agent Discovery** | Separate API | Offline discovery | Agent Cards |
| **Authentication** | OAuth 2.0 | Multiple methods | OAuth/JWT |
| **Governance** | Open | Linux Foundation | Google-led |
| **Multimodal Support** | Multiple part types | Native | Multiple formats |
| **Current Status** | Active development | Active development | Active development |

## Project Repositories

- [**ARC Protocol**](https://github.com/arcprotocol/arcprotocol) - Agent communication protocol
- [**ARC Ledger**](https://github.com/arcprotocol/arcledger) - Agent discovery registry
- [**ARC Compass**](https://github.com/arcprotocol/arccompass) - Agent search engine


## Community

- [**Discord**](https://discord.gg/arcprotocol) - Join our community chat
- [**Twitter**](https://twitter.com/arcprotocol) - Follow for updates
- [**GitHub Discussions**](https://github.com/arcprotocol/arc-protocol/discussions) - Ask questions and share ideas

---

<p align="center">
  <a href="https://arc-protocol.org">Website</a> •
  <a href="https://docs.arc-protocol.org">Documentation</a> •
  <a href="https://github.com/arcprotocol/arc-protocol/discussions">Discussions</a> •
  <a href="https://discord.gg/arcprotocol">Discord</a>
</p>