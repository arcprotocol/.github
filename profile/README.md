# Agent Remote Communication (ARC) Protocol

# <img src="../assets/arc_banner.jpeg" alt="ARC Protocol" width="100%">

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![GitHub stars](https://img.shields.io/github/stars/arcprotocol/arcprotocol.svg?style=social&label=Star)](https://github.com/arcprotocol/arcprotocol)
[![Discord](https://img.shields.io/discord/1234567890?color=7289da&label=Discord&logo=discord)](https://discord.gg/XYmp22xX5m)
[![Twitter Follow](https://img.shields.io/twitter/follow/arcprotocol?style=social)](https://twitter.com/arcprotocol)

## 🚀 The First Multi-Agent Communication Protocol

**ARC (Agent Remote Communication)** is the first RPC protocol that solves multi-agent deployment complexity with built-in agent routing, load balancing, and workflow tracing. Deploy hundreds of different agent types on a single endpoint with zero infrastructure overhead - no service discovery, no API gateways, no orchestration engines required.

> "ARC Protocol is to agent communication what HTTP was to the web - a simple, universal standard that unlocks an entire ecosystem." 

## 🌟 Why ARC Protocol?

### 🏗️ **Single Endpoint, Multiple Agents**
Deploy 10s or 100s of agents behind `https://company.com/arc` - no need for separate endpoints per agent

### 🔄 **Built-in Agent Routing**
Automatic routing via `requestAgent` and `targetAgent` fields - no need for custom routing logic

### 📊 **Load Balancing Ready**
Route to `finance-agent-01`, `finance-agent-02`, `finance-agent-03` automatically

### 🔍 **End-to-End Workflow Tracing**
Track complex workflows across multiple agent interactions with `traceId`

### 🔐 **Enterprise-Grade Security**
OAuth2 scopes designed for agent-to-agent communication

### 🧩 **Comprehensive Error Handling**
500+ categorized error codes with detailed context for debugging and monitoring

## 📚 Protocol Specification

The ARC Protocol is defined in the [Official Specification](https://github.com/arcprotocol/arc-protocol/blob/main/ARC-Protocol-Official-Specification.md), which details:

- **Message Structure**: Request and response formats
- **Method Definitions**: 9 standard methods across task, chat, and notification categories
- **Data Types**: Message, Part, Artifact, and other core types
- **Authentication**: OAuth2 scope patterns for agent permissions
- **Error Handling**: Comprehensive error code system

## 🛠️ SDK Implementations

ARC Protocol is available in multiple languages:

- [**Python SDK**](https://github.com/arcprotocol/python-sdk) - `pip install arc-sdk`
- [**JavaScript SDK**](https://github.com/arcprotocol/js-sdk) - `npm install @arcprotocol/sdk`
- [**Go SDK**](https://github.com/arcprotocol/go-sdk) - `go get github.com/arcprotocol/go-sdk`
- More languages coming soon!

## 🎯 Key Features

### **Task Methods (Asynchronous)**
For long-running operations like document analysis, report generation:

```python
# Create a new task
task = await client.task.create(
    target_agent="document-analyzer-01",
    initial_message={"role": "user", "parts": [{"type": "TextPart", "content": "Analyze quarterly report"}]}
)

# Check progress
status = await client.task.info(task_id=task.taskId)
```

### **Chat Methods (Real-time)**
For interactive conversations and real-time data:

```python
# Start a real-time conversation
chat = await client.chat.start(
    target_agent="support-agent-01",
    initial_message={"role": "user", "parts": [{"type": "TextPart", "content": "Help with my account"}]},
    stream=True
)

# Continue conversation
await client.chat.message(chat_id=chat.chatId, message=follow_up_message, stream=True)
```

### **Multi-Agent Workflows**
Connect multiple agents with automatic tracing:

```python
# Step 1: Document analysis
doc_task = await client.task.create(
    target_agent="document-analyzer-01",
    initial_message={"role": "user", "parts": [{"type": "FilePart", "content": pdf_content}]},
    trace_id="workflow_quarterly_report_789"
)

# Step 2: Chart generation (same trace_id connects the workflow)
chart_task = await client.task.create(
    target_agent="chart-generator-01",
    initial_message={"role": "agent", "parts": [{"type": "DataPart", "content": extracted_data}]},
    trace_id="workflow_quarterly_report_789"  # Same trace_id!
)
```

## 🏢 Enterprise Use Cases

### **Financial Services**
- **Multi-agent credit analysis**: Document extraction → Financial analysis → Risk assessment → Report generation
- **Real-time trading assistants**: Market data streams → Analysis → Recommendations

### **Healthcare**
- **Patient data processing**: Medical records → Diagnosis assistance → Treatment recommendations
- **Medical imaging workflow**: Image processing → Analysis → Report generation

### **Customer Support**
- **Tiered support system**: Initial triage → Specialist routing → Resolution tracking
- **Multi-channel support**: Email, chat, voice unified through single protocol

## 📈 Comparison to Existing Protocols

| Feature | ARC | ACP (Agent Communication Protocol) | A2A (Agent-to-Agent) | JSON-RPC 2.0 | gRPC | REST |
|---------|-----|-----------------------------------|----------------------|---------------|------|------|
| **Agent Routing** | ✅ Built-in | ✅ REST-based | ✅ Built-in | ❌ Manual | ❌ Manual | ❌ Manual |
| **Workflow Tracing** | ✅ Native | ✅ Built-in | ✅ Task tracking | ❌ Custom | ⚠️ External | ❌ Custom |
| **Multi-Agent Ready** | ✅ First-class | ✅ First-class | ✅ First-class | ❌ DIY | ❌ DIY | ❌ DIY |
| **Load Balancing** | ✅ Protocol-level | ⚠️ Server-based | ✅ Agent Cards | ❌ External | ❌ External | ❌ External |
| **Learning Curve** | ✅ Simple | ✅ Simple | ✅ Moderate | ✅ Simple | ❌ Complex | ✅ Simple |
| **Governance** | Open | Linux Foundation | Google-led | Open | Google-led | Open |

## 🤝 Contributing

We welcome contributions from the community! See our [Contributing Guidelines](.github/CONTRIBUTING.md) and [Code of Conduct](.github/CODE_OF_CONDUCT.md).

## 📄 License

ARC Protocol is licensed under the [Apache License 2.0](LICENSE).

## 🌐 Community

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