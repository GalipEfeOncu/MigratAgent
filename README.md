<div align="center">

<img src="https://img.shields.io/badge/version-0.1.0--alpha-blueviolet?style=for-the-badge" alt="Version">
<img src="https://img.shields.io/badge/python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
<img src="https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi" alt="FastAPI">
<img src="https://img.shields.io/badge/LangGraph-FF6B35?style=for-the-badge&logo=chainlink&logoColor=white" alt="LangGraph">
<img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker">
<img src="https://img.shields.io/badge/license-Apache_2.0-green?style=for-the-badge" alt="License">

<br/><br/>

<h1>⚡ MigratAgent</h1>
<h3>The Autonomous Tech-Stack Migration Engine</h3>

<p>A self-correcting, multi-agent AI system that autonomously migrates legacy codebases<br>to modern <strong>FastAPI</strong> architecture — complete with clean code, tests, and a performance report.</p>

<br/>

[**Get Started**](#-quickstart) · [**Architecture**](docs/architecture.md) · [**Agents**](docs/agents.md) · [**Roadmap**](docs/roadmap.md) · [**Contributing**](CONTRIBUTING.md)

<br/>

</div>

---

## 🧠 The Problem

Large-scale companies carry a silent burden: millions of lines of **legacy code** written in outdated languages and frameworks. Migrating these systems manually takes months, burns enormous budgets, and almost always results in lost business logic.

> **MigratAgent eliminates this.** It reads your old code, understands its intent, and rewrites it from scratch in a clean, modern, production-ready FastAPI architecture — autonomously.

---

## ✨ Key Features

| Feature | Description |
|---|---|
| 🔍 **Language-Agnostic Analysis** | Parses and extracts business logic regardless of the input language |
| 🏛️ **Clean Architecture Output** | Generates FastAPI code with Dependency Injection, Pydantic v2 schemas, and async/await |
| 🔄 **Self-Correction Loop** | If generated tests fail, the error is fed back to the Coder agent — it loops until green |
| 🧪 **Auto-Generated Tests** | Produces and *runs* Pytest suites for every migrated module |
| 🎯 **Confidence Scoring** | Each migrated component receives a confidence score — flags low-confidence sections for human review |
| 📊 **Performance Report** | Benchmarks the original vs. migrated code and delivers a performance gain summary |
| 📡 **Real-time Streaming** | Watch the migration unfold live via WebSocket stream |
| 🔒 **Sandboxed Execution** | All generated code is executed inside isolated Docker containers — zero risk to the host |
| 🔭 **Full Observability** | Every agent decision is traced via LangSmith for complete auditability |

---

## 🏗️ System Architecture

MigratAgent is built on a **stateful, cyclic multi-agent graph** orchestrated by LangGraph. Four specialized agents collaborate in a structured pipeline:

```
┌──────────────────────────────────────────────────────────────────┐
│                        MigratAgent Pipeline                       │
│                                                                    │
│   Legacy Code                                                      │
│       │                                                            │
│       ▼                                                            │
│  ┌─────────────┐     Business      ┌─────────────────┐            │
│  │  🔍 Analyst  │ ─── Logic ──────▶ │  🏛️ Architect   │            │
│  │             │     Schema         │                 │            │
│  └─────────────┘                   └────────┬────────┘            │
│                                             │ File & Module Plan   │
│                                             ▼                      │
│                                    ┌─────────────────┐            │
│                        ◀─ Errors ─ │   💻 Coder       │            │
│                        │           │                 │            │
│                        │           └────────┬────────┘            │
│                        │                    │ Generated Code       │
│                        │                    ▼                      │
│                        │           ┌─────────────────┐            │
│                        └─────────  │   🧪 Tester      │            │
│                                    │  (Sandboxed)    │            │
│                                    └────────┬────────┘            │
│                                             │ All Tests Green ✅   │
│                                             ▼                      │
│                                    Migration Report + Output       │
└──────────────────────────────────────────────────────────────────┘
```

### The Four Agents

| Agent | Role |
|---|---|
| 🔍 **Analyst** | Parses the input code, ignoring syntax, to extract database relationships, business rules, and API contracts into a structured markdown schema |
| 🏛️ **Architect** | Translates the schema into a modern FastAPI file plan: routers, services, repositories, schemas, and dependency injection wiring |
| 💻 **Coder** | Implements the plan — writing fully async, type-annotated, PEP8-compliant Python code faithful to the architecture |
| 🧪 **Tester** | Generates Pytest test suites, executes them in a Docker sandbox, and feeds any failures back to the Coder. The loop continues until all tests pass |

---

## 🛠️ Tech Stack

**Backend & API**
- [Python 3.11+](https://www.python.org/)
- [FastAPI](https://fastapi.tiangolo.com/) — Async API framework
- [Pydantic v2](https://docs.pydantic.dev/latest/) — Data validation & settings

**AI & Agent Orchestration**
- [LangGraph](https://www.langchain.com/langgraph) — Stateful, cyclic multi-agent graphs
- [LangChain](https://www.langchain.com/) — LLM abstraction layer
- [OpenAI API](https://platform.openai.com/) — Primary LLM / [Ollama](https://ollama.com/) for local runs

**Testing & Execution**
- [Pytest](https://pytest.org/) — Test framework
- [Docker](https://www.docker.com/) — Sandboxed code execution

**Observability**
- [LangSmith](https://smith.langchain.com/) — Agent tracing & evaluation

---

## 🚀 Quickstart

> ⚠️ **Status:** This project is currently in active development. The steps below reflect the planned setup flow.

### Prerequisites

- Python 3.11+
- Docker
- OpenAI API key (or Ollama running locally)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/GalipEfeOncu/MigratAgent.git
cd MigratAgent

# 2. Install dependencies
pip install -e ".[dev]"

# 3. Configure environment
cp .env.example .env
# Edit .env with your API keys

# 4. Start the API server
make run
```

### Run Your First Migration

```bash
# Via CLI
python -m migrat_agent migrate --input examples/legacy_flask_app/ --target fastapi

# Via API (after server is running)
curl -X POST http://localhost:8000/api/v1/migrate \
  -H "Content-Type: application/json" \
  -d '{"source_code": "...", "source_framework": "flask"}'
```

---

## 📁 Project Structure

```
MigratAgent/
├── src/migrat_agent/
│   ├── agents/          # The four core agents
│   │   ├── analyst.py
│   │   ├── architect.py
│   │   ├── coder.py
│   │   └── tester.py
│   ├── graph/           # LangGraph state & workflow
│   │   ├── state.py
│   │   └── workflow.py
│   ├── core/            # LLM client & prompt templates
│   ├── schemas/         # Pydantic models
│   ├── services/        # Business logic & sandbox manager
│   ├── api/             # FastAPI routers & endpoints
│   └── utils/           # Logger & helpers
├── tests/
│   ├── unit/
│   └── integration/
├── docs/
│   ├── architecture.md
│   ├── agents.md
│   ├── roadmap.md
│   ├── setup.md
│   ├── api-reference.md
│   └── decisions/       # Architecture Decision Records (ADRs)
├── examples/            # Sample legacy code inputs
└── scripts/             # Dev & utility scripts
```

---

## 🗺️ Roadmap

- [x] **Phase 0** — Project scaffolding & architecture design
- [ ] **Phase 1 — MVP** · Analyst + Coder agents · Flask → FastAPI migration · CLI interface
- [ ] **Phase 2 — Self-Correction** · Tester agent · Pytest integration · Self-correction loop
- [ ] **Phase 3 — Production Grade** · Architect agent · Docker sandboxing · LangSmith tracing · WebSocket streaming
- [ ] **Phase 4 — Showcase** · Confidence scoring · Benchmark reports · Video demo

See the full plan in [docs/roadmap.md](docs/roadmap.md).

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting a pull request.

---

## 📄 License

Distributed under the Apache 2.0 License. See [LICENSE](LICENSE) for more information.

---

<div align="center">
  <sub>Built with 🤖 and ☕ by <a href="https://github.com/GalipEfeOncu">Galip Efe Öncu</a></sub>
</div>