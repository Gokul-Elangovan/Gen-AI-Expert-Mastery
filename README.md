# 🚀 Gen AI Expert + Anthropic Claude Certified Architect — Master Roadmap

> **Owner:** AI Agents Developer → Gen AI Expert + Anthropic Claude Certified Architect + Product-Based SDE
> **Started:** May 2026
> **Goal:** Master Gen AI end-to-end, earn Anthropic Claude Certified Architect credential, build production-grade projects, crack product-based company interviews
> **Golden Rule:** _No random YouTube marathons. Follow the phases. Check the boxes. Ship projects._

---

## 🏆 Certification Target

### Anthropic Claude Certified Architect
> The Anthropic Claude Certified Architect credential validates your ability to design, build, and deploy sophisticated AI systems using Claude — from API fundamentals through multi-agent architectures, safety, and production operations.

**Exam domains (weighted):**

| Domain | Weight | Your Phase |
|---|---|---|
| Claude API & SDK mastery | 20% | Phase 2-C |
| Prompt engineering & structured outputs | 15% | Phase 2-B |
| Tool use & function calling | 20% | Phase 3-A |
| Multi-agent system design (MCP, orchestration) | 20% | Phase 3-B |
| Safety, Constitutional AI & guardrails | 10% | Phase 3-C |
| Production architecture (caching, cost, observability) | 15% | Phase 4-D |

**Certification prep resources (official):**
- [docs.anthropic.com](https://docs.anthropic.com) — primary reference
- [Anthropic Cookbook (GitHub)](https://github.com/anthropics/anthropic-cookbook) — hands-on patterns
- [Anthropic Courses (GitHub)](https://github.com/anthropics/courses) — official curriculum
- [Model Context Protocol docs](https://modelcontextprotocol.io) — MCP specification
- [Claude's Constitution](https://www.anthropic.com/research/claude-s-constitution) — safety & values

---

## 📌 Current Reality Check

| Area | Status |
|---|---|
| Python fundamentals | Moderate — gaps in advanced concepts |
| DSA | Weak — needs structured daily practice |
| AI Agents (LangChain/LangGraph) | Working knowledge — can't build from scratch confidently |
| FastAPI / Backend | Beginner — needs hands-on projects |
| Databases (SQL/NoSQL) | Basics — needs production patterns |
| System Design | Not started |
| Production-Grade Deployment | Not started |
| Gen AI (LLMs, RAG, Fine-tuning) | Conceptual — needs depth |
| **Claude API & tool use** | **Not started — certification gap** |
| **MCP & multi-agent with Claude** | **Not started — certification gap** |
| **Claude safety & Constitutional AI** | **Not started — certification gap** |

---

## 🗺️ Roadmap Overview (8-Month Plan)

```
Month 1-2  ▶  PHASE 1: Python Mastery + DSA Foundation + FastAPI Basics
Month 2-3  ▶  PHASE 2: Gen AI Deep Dive + Claude API Mastery ← CERT TRACK BEGINS
Month 3-4  ▶  PHASE 3: AI Agents Mastery + Claude Tool Use + MCP ← CERT CORE
Month 4-5  ▶  PHASE 4: Backend + Databases + System Design + Claude Prod Architecture
Month 5-6  ▶  PHASE 5: Production-Grade Projects (Claude-native) + Interview Prep
Month 6-7  ▶  PHASE 6: Certification Sprint — Mock exams, case studies, final gaps
Month 7-8  ▶  PHASE 7: Post-cert leverage — advanced projects, talks, contributions
Ongoing    ▶  PHASE 8: DSA Daily Practice (runs parallel from Day 1)
```

---

## 📅 Daily Routine Template

| Time Block | Activity | Duration |
|---|---|---|
| 🌅 Morning | DSA Problem Solving (LeetCode/NeetCode) | 1–1.5 hrs |
| 🌤️ Mid-Morning | Current Phase Learning (theory + notes) | 2 hrs |
| 🌞 Afternoon | Hands-On Coding / Project Work | 2–3 hrs |
| 🌆 Evening | Revision (Anki cards / quick notes review) | 30 min |
| 🌙 Night | System Design reading / Mock interviews (weekend) | 1 hr |

> ⚡ **Anti-Comfort-Zone Rule:** If you skip 2 days in a row, restart the current week's plan from scratch. No exceptions.

---

## 🔥 PHASE 1 — Python Mastery + DSA Foundation + FastAPI Basics

**Duration:** Weeks 1–8
**Goal:** Solid Python, confident with 100+ DSA problems, basic REST APIs with FastAPI

### 1.1 Python Advanced Concepts
- [ ] Decorators & closures — build 3 custom decorators
- [ ] Generators & iterators — implement lazy data pipeline
- [ ] Context managers — build custom file handler & DB connection manager
- [ ] `*args, **kwargs` — deep understanding with 5 practice exercises
- [ ] OOP — Inheritance, Polymorphism, Abstract Classes, Dunder methods
- [ ] Type hints & Pydantic models — validate 5 different data schemas
- [ ] Error handling patterns — custom exceptions, retry logic
- [ ] `asyncio` fundamentals — async/await, event loop, tasks
- [ ] Concurrency — threading vs multiprocessing vs asyncio (know when to use what)
- [ ] Python project structure — `__init__.py`, packages, relative imports
- [ ] Virtual environments & dependency management (venv, poetry)
- [ ] **Mini-Project:** CLI tool that processes CSV files with async I/O

### 1.2 DSA Foundation (LeetCode Grind Starts Here)
- [ ] Arrays & Hashing — 15 problems
- [ ] Two Pointers — 10 problems
- [ ] Sliding Window — 10 problems
- [ ] Stacks & Queues — 10 problems
- [ ] Binary Search — 10 problems
- [ ] Linked Lists — 10 problems
- [ ] Trees (BFS/DFS) — 15 problems
- [ ] Graphs (BFS/DFS/Topological Sort) — 10 problems
- [ ] Dynamic Programming (1D) — 10 problems
- [ ] **Tracker:** Use NeetCode 150 or Striver's SDE Sheet

### 1.3 FastAPI Basics
- [ ] Setup FastAPI project with proper structure
- [ ] Path params, query params, request body
- [ ] Pydantic models for request/response validation
- [ ] CRUD API for a simple entity (e.g., notes/tasks)
- [ ] Dependency injection pattern
- [ ] Middleware & error handling
- [ ] Background tasks
- [ ] **Mini-Project:** Task Manager REST API with in-memory storage

---

## 🧠 PHASE 2 — Gen AI Deep Dive + Claude API Mastery

**Duration:** Weeks 9–16
**Goal:** Understand LLMs from the ground up, build RAG systems, master prompt engineering, and achieve deep Claude API fluency

> 🎯 **Certification note:** Sections 2-C and 2-D are exclusively Claude-focused and map directly to the Anthropic certification exam.

### 2.1 LLM Fundamentals
- [ ] How Transformers work — attention mechanism, tokenization
- [ ] GPT architecture — decoder-only, autoregressive generation
- [ ] Token limits, temperature, top-p, frequency penalty — experiment hands-on
- [ ] Embedding models — what they are, when to use them
- [ ] Streaming responses — implement in Python
- [ ] **Mini-Project:** Direct API chatbot with streaming, multi-turn conversation

### 2.2 Prompt Engineering Mastery
- [ ] Zero-shot, few-shot, chain-of-thought prompting
- [ ] System prompts — structuring behavior and persona
- [ ] Output formatting — JSON mode, structured outputs with Pydantic
- [ ] Prompt chaining — breaking complex tasks into steps
- [ ] Guardrails & safety — input validation, output filtering
- [ ] **Mini-Project:** Automated resume analyzer using prompt chaining

### 2.3 Claude API Deep Mastery ★ CERT TRACK
- [ ] Install `anthropic` SDK — understand client setup, API keys, env management
- [ ] Messages API — `model`, `max_tokens`, `system`, `messages` structure
- [ ] Content blocks — text, image, document types; multi-modal inputs
- [ ] Streaming with `client.messages.stream()` — handle `text_delta`, `input_json_delta` events
- [ ] Token counting — `client.messages.count_tokens()` before sending
- [ ] Vision — send images as base64 or URL; use for document understanding
- [ ] Batch API — `client.messages.batches.create()` for async bulk processing (50% cost saving)
- [ ] **Prompt caching** — `cache_control: {type: "ephemeral"}` on large system prompts; understand 5-min TTL
- [ ] Model selection strategy — when to use Opus 4 vs Sonnet 4 vs Haiku 4.5; cost vs capability trade-off
- [ ] Error handling — rate limits (429), overload (529), API errors — implement exponential backoff
- [ ] **Mini-Project:** Build a streaming document analyzer with prompt caching that reduces costs by 60%+

### 2.4 Claude Prompt Engineering — Certified Patterns ★ CERT TRACK
- [ ] XML tag structuring — `<document>`, `<instructions>`, `<examples>`, `<output>` — Claude responds best to XML
- [ ] System prompt architecture — role, task, context, output format, constraints
- [ ] Chain-of-thought with `<thinking>` tags — when to use extended thinking mode
- [ ] Extended thinking — `thinking: {type: "enabled", budget_tokens: 10000}` — for complex reasoning
- [ ] Structured outputs — force JSON via `tools` with output schema (most reliable method)
- [ ] Prefilling responses — start assistant turn to steer output format
- [ ] Avoiding hallucinations — citation patterns, "I don't know" instructions
- [ ] **Meta-prompt pattern** — have Claude write its own system prompt for a task
- [ ] **Mini-Project:** Prompt library of 10 certified patterns with eval suite

### 2.5 RAG Systems
- [ ] What is RAG — architecture overview
- [ ] Document loaders — PDF, web, markdown, CSV
- [ ] Text splitting strategies — chunk size, overlap, semantic chunking
- [ ] Vector databases — ChromaDB, Pinecone, Weaviate (pick 2)
- [ ] Embedding + similarity search — cosine similarity, MMR
- [ ] RAG pipeline — query → retrieve → augment → generate
- [ ] Advanced RAG — re-ranking, hybrid search, HyDE, query transformation
- [ ] Evaluation — faithfulness, relevancy, RAGAS framework
- [ ] **Project:** Q&A system over your own documents using Claude + ChromaDB

### 2.6 Fine-Tuning Basics
- [ ] When to fine-tune vs when to use RAG vs prompt engineering
- [ ] LoRA & QLoRA concepts
- [ ] Fine-tune a small open-source model on custom dataset (Hugging Face)
- [ ] Evaluate fine-tuned model vs base model

---

## 🤖 PHASE 3 — AI Agents Mastery + Claude Tool Use + MCP

**Duration:** Weeks 17–24
**Goal:** Build production-quality Claude-native agents from scratch, master tool use, MCP, and multi-agent safety

> 🎯 **Certification note:** This entire phase is high-weight exam content. Build every project. Understand every component at the code level.

### 3.1 Claude Tool Use — Complete Mastery ★ CERT TRACK
- [ ] Tool definition schema — `name`, `description`, `input_schema` (JSON Schema)
- [ ] Writing tool descriptions — the description IS the instruction; write like a docstring
- [ ] Single tool call — handle `stop_reason: "tool_use"`, extract `tool_use` block
- [ ] Tool result injection — `role: user`, `type: tool_result`, `tool_use_id` matching
- [ ] Multi-turn tool loop — implement the full ReAct loop with raw API calls
- [ ] **Parallel tool calls** — Claude can call multiple tools simultaneously; handle array of tool_use blocks
- [ ] Forced tool use — `tool_choice: {type: "any"}` or `{type: "tool", name: "..."}` 
- [ ] Tool error handling — `is_error: true` in tool_result; graceful degradation
- [ ] Streaming with tools — handle `input_json_delta` events to stream tool inputs
- [ ] Computer use tools — `bash`, `computer`, `text_editor` tool types (Claude 3.5+)
- [ ] **Mini-Project:** Build a research agent with 5 tools (web search, calculator, file read/write, code exec) from scratch — no LangChain

### 3.2 Model Context Protocol (MCP) ★ CERT TRACK
- [ ] What is MCP — open standard for tool/resource/prompt serving to any LLM client
- [ ] MCP architecture — host, client, server; transport types (stdio, SSE)
- [ ] MCP primitives — **Tools** (execute actions), **Resources** (read data), **Prompts** (reusable templates), **Sampling** (LLM calls from server)
- [ ] Build an MCP server in Python with `mcp` SDK — expose 3+ custom tools
- [ ] Build an MCP server in Node.js — understand both runtimes
- [ ] Connect MCP server to Claude Desktop / Claude Code
- [ ] MCP Resources — expose files, DB records, API data as context
- [ ] MCP Prompts — reusable prompt templates with arguments
- [ ] MCP Sampling — let the server call Claude for sub-tasks (agent-to-agent)
- [ ] Security — MCP tool call confirmation, minimal permission principle
- [ ] **Project:** Build a production MCP server that connects Claude to a PostgreSQL database — list tables, run queries, generate schema diagrams

### 3.3 Multi-Agent Architectures with Claude ★ CERT TRACK
- [ ] Why multi-agent — parallelization, specialization, verification patterns
- [ ] **Orchestrator-subagent pattern** — one Claude instance routes to specialized Claude instances
- [ ] **Parallelization pattern** — spawn multiple Claude agents for concurrent tasks; aggregate results
- [ ] **Evaluator-optimizer loop** — one agent generates, another critiques, loop until quality gate passes
- [ ] Human-in-the-loop — when and how to pause for approval; `interrupt` patterns
- [ ] Agent state management — how to persist state across turns (DB, Redis, in-memory)
- [ ] Minimal footprint principle — agents should request only needed permissions; prefer reversible actions
- [ ] Prompt injection defense in agentic contexts — validate tool outputs before feeding back
- [ ] LangGraph for Claude — `StateGraph`, conditional edges, `interrupt_before`, checkpointing with Claude as LLM
- [ ] **Project:** Multi-agent research pipeline — Planner (decomposes task) → 3× Researcher agents (parallel) → Synthesizer → Fact-checker; all using Claude

### 3.4 Constitutional AI & Safety ★ CERT TRACK
- [ ] What is Constitutional AI (CAI) — principles, critique-revision loop
- [ ] Anthropic's model spec — Claude's values, what it will/won't do, why
- [ ] Hardcoded vs softcoded behaviors — what operators/users can and cannot change
- [ ] System prompt safety design — operator trust level, user trust level
- [ ] Input guardrails — detect jailbreaks, prompt injection, off-topic requests
- [ ] Output guardrails — check for PII, harmful content, hallucinations before returning
- [ ] Sensitive topic handling — how Claude handles CSAM, CBRN, political content
- [ ] **Audit trail design** — log every agent action for human review
- [ ] **Mini-Project:** Build a guardrails wrapper around Claude that blocks 10 categories of unsafe input/output

### 3.5 LangChain Deep Dive (Framework Layer)
- [ ] LangChain Expression Language (LCEL) — pipes, runnables, chains
- [ ] Chat models — structured outputs, tool calling via LangChain abstraction
- [ ] Output parsers — Pydantic, JSON, CSV
- [ ] Prompt templates — ChatPromptTemplate, MessagesPlaceholder
- [ ] Retrievers — vector store, multi-query, ensemble
- [ ] Memory — ConversationBufferMemory, Summary, Entity
- [ ] Callbacks & tracing — LangSmith integration
- [ ] **Project:** Multi-document chatbot with memory & citations using Claude + LangChain

---

## 🏗️ PHASE 4 — Backend + Databases + System Design + Claude Production Architecture

**Duration:** Weeks 25–32
**Goal:** Build production-grade backends, understand databases deeply, design AI systems at scale

> 🎯 **Certification note:** Section 4.4 is exam-critical — production Claude architecture is heavily tested.

### 4.1 FastAPI Advanced
- [ ] Authentication — JWT, OAuth2 with FastAPI
- [ ] Database integration — SQLAlchemy ORM + Alembic migrations
- [ ] Async database queries — asyncpg, databases library
- [ ] File uploads & storage (S3-compatible)
- [ ] WebSocket support — real-time streaming Claude responses
- [ ] Rate limiting & caching (Redis)
- [ ] Testing — pytest, TestClient, mocking
- [ ] API versioning & documentation
- [ ] **Project:** Full authentication system with role-based access

### 4.2 Databases
- [ ] PostgreSQL — advanced queries, indexing, EXPLAIN ANALYZE
- [ ] Database design — normalization, denormalization trade-offs
- [ ] Redis — caching patterns, pub/sub, session storage
- [ ] MongoDB — when to use NoSQL, document modeling
- [ ] Vector databases deep dive — indexing strategies (HNSW, IVF)
- [ ] Connection pooling, transactions, ACID properties
- [ ] **Project:** Design and implement DB schema for an AI chatbot platform with conversation history

### 4.3 System Design
- [ ] Fundamentals — scalability, availability, consistency (CAP theorem)
- [ ] Load balancers, CDNs, caching layers
- [ ] Message queues — RabbitMQ, Kafka basics
- [ ] Microservices vs monolith — when to use what
- [ ] API Gateway patterns
- [ ] Rate limiting & circuit breaker patterns
- [ ] Design a URL shortener
- [ ] Design a chat application
- [ ] Design a notification system
- [ ] **Design an AI-powered document Q&A platform (your specialty!)**
- [ ] Study: "System Design Interview" by Alex Xu (Vol 1 & 2)

### 4.4 Production Claude Architecture ★ CERT TRACK
- [ ] **Prompt caching strategy** — identify cacheable prefixes (system prompt, documents, tools); measure cache hit rate with `cache_read_input_tokens`
- [ ] **Cost optimization** — Haiku for routing/classification, Sonnet for agents, Opus for complex reasoning; hybrid model routing
- [ ] **Latency optimization** — streaming for perceived latency; parallel tool calls; async batch for non-realtime
- [ ] **Observability** — trace every Claude call with LangSmith or Langfuse; log input/output tokens, latency, cost per request
- [ ] **Rate limit management** — token bucket pattern, queue with priority levels, exponential backoff with jitter
- [ ] **Context window management** — summarization for long conversations; sliding window; selective context injection
- [ ] **Eval pipeline** — automated evals with `claude-haiku` as judge; regression testing on prompt changes
- [ ] **A/B testing prompts** — experiment framework for prompt variants; measure quality vs cost
- [ ] **Production checklist:** No secrets in prompts, PII scrubbing before logging, output validation before returning to user
- [ ] **Mini-Project:** Build a cost dashboard that tracks per-request Claude spend with prompt cache hit rate

---

## 🚢 PHASE 5 — Production-Grade Claude Projects + Interview Prep

**Duration:** Weeks 33–40
**Goal:** Ship 3 portfolio-worthy Claude-native projects, drill interviews, demonstrate architect-level thinking

### 5.1 Production Skills
- [ ] Docker — containerize your apps
- [ ] Docker Compose — multi-service setup (app + db + redis)
- [ ] CI/CD — GitHub Actions pipeline
- [ ] Logging & monitoring — structured logging, basic observability
- [ ] Error tracking — Sentry integration
- [ ] Environment management — .env, secrets management
- [ ] Cloud deployment — AWS (EC2, S3, RDS) or GCP basics
- [ ] Cost optimization for LLM applications

### 5.2 Portfolio Projects (Build, Deploy & Demo These)

#### 🏆 Project 1: AI-Powered Document Intelligence Platform (Claude-Native)
**Cert relevance:** RAG + Claude API + prompt caching + streaming
- [ ] Multi-format document ingestion (PDF, DOCX, web)
- [ ] Advanced RAG with hybrid search & re-ranking via Claude
- [ ] **Prompt caching** on large document corpus — demonstrate 60%+ cost reduction
- [ ] FastAPI backend with auth & rate limiting
- [ ] PostgreSQL + ChromaDB/Pinecone
- [ ] **Streaming responses** via WebSocket using `client.messages.stream()`
- [ ] LangSmith tracing in production — full observability
- [ ] Docker + cloud deployment
- [ ] Eval suite with RAGAS metrics

#### 🏆 Project 2: MCP-Powered Personal AI Workspace
**Cert relevance:** MCP + tool use + multi-agent
- [ ] Custom MCP server exposing: file system, Google Calendar, GitHub, Notion
- [ ] Claude Desktop integration — works as a local AI assistant
- [ ] Tool use with 10+ tools — web search, code exec, email, calendar, git
- [ ] **Parallel tool calls** — multiple actions executed simultaneously
- [ ] Memory & personalization layer (user preferences, past actions)
- [ ] Usage analytics dashboard
- [ ] Comprehensive test suite for MCP server tools

#### 🏆 Project 3: Multi-Agent Workflow Engine with Claude Orchestration
**Cert relevance:** Multi-agent patterns + LangGraph + safety + human-in-the-loop
- [ ] LangGraph-based orchestration with Claude as all agents
- [ ] Agents: Planner, Researcher (parallel ×3), Analyst, Writer, Fact-Checker
- [ ] **Evaluator-optimizer loop** — automated quality gate before output
- [ ] Human-in-the-loop approval for high-stakes actions
- [ ] Persistent state — resume interrupted workflows
- [ ] FastAPI backend + real-time WebSocket updates
- [ ] Full guardrails — input validation, output safety checks, audit log
- [ ] Production monitoring with per-agent cost tracking

### 5.3 Interview Preparation
- [ ] DSA — reach 200+ LeetCode problems (medium focus)
- [ ] System Design — practice 10 designs with timer (45 min each)
- [ ] ML basics — regression, classification, evaluation metrics
- [ ] **20 Claude/Gen AI interview questions** — see Section 5.4 below
- [ ] Behavioral — STAR method, prepare 10 stories
- [ ] Resume — highlight projects with metrics & impact (cost saved, latency, accuracy)
- [ ] Mock interviews — schedule 2 per week

### 5.4 Claude & Gen AI Interview Question Bank ★ CERT PREP
Prepare detailed answers for all of these:

**Claude API & fundamentals**
- [ ] How does Claude's tool use cycle work? Walk me through a multi-turn example.
- [ ] What is prompt caching and when should you use it? What are its limitations?
- [ ] How does the extended thinking mode work and when is it worth the extra cost?
- [ ] How do you choose between Haiku, Sonnet, and Opus for different tasks in a production system?
- [ ] How do you handle rate limits and API errors in a production Claude integration?

**Agents & multi-agent**
- [ ] Explain the orchestrator-subagent pattern. When does it break down?
- [ ] What is MCP? How is it different from just defining tools in the API?
- [ ] How do you prevent prompt injection attacks in agentic systems?
- [ ] What is the "minimal footprint" principle for agents? Give a design example.
- [ ] When would you use parallel tool calls vs sequential tool calls?

**Safety & production**
- [ ] What is Constitutional AI? How does it influence Claude's behavior?
- [ ] What is the difference between hardcoded and softcoded behaviors in Claude?
- [ ] How would you design a guardrails layer for an enterprise Claude deployment?
- [ ] How do you build an eval pipeline for a RAG system powered by Claude?
- [ ] How would you architect a Claude-based system to handle 1M requests/day within budget?

**System design (AI-specific)**
- [ ] Design an AI document Q&A platform that serves 100k users. Walk through every component.
- [ ] How would you implement conversation memory for a Claude-based assistant at scale?
- [ ] Design a multi-agent system for automated code review. What agents do you need?
- [ ] How do you detect and handle context window exhaustion in a long-running agent?
- [ ] What metrics do you track in production for an LLM-powered feature?

---

## 🎓 PHASE 6 — Certification Sprint

**Duration:** Weeks 41–46 (6 weeks dedicated)
**Goal:** Systematic exam preparation, plug all gaps, pass the Anthropic Claude Certified Architect exam

### 6.1 Domain-by-Domain Revision

| Domain | Week | Activities |
|---|---|---|
| Claude API & SDK | Week 41 | Re-read all official docs; run every code example; build from memory |
| Prompt engineering | Week 41 | Rebuild prompt library; practice structured output patterns |
| Tool use & function calling | Week 42 | Implement 3 agents from scratch without references |
| MCP & multi-agent | Week 42 | Build full MCP server; design 2 multi-agent architectures |
| Safety & Constitutional AI | Week 43 | Read Anthropic model spec; implement guardrails layer |
| Production architecture | Week 43 | Cost/latency analysis exercise; design production system |
| Mock exams | Weeks 44–45 | Timed case studies; peer review; gap analysis |
| Final review | Week 46 | Weak areas only; flashcard drill; rest before exam |

### 6.2 Practical Exam Exercises
- [ ] **Exercise 1:** Given a use case (e.g., legal document review), design the full Claude architecture — tools, prompts, agents, cost estimate, eval plan — in 45 minutes
- [ ] **Exercise 2:** Debug a broken tool use loop from a code snippet — identify the 3 errors
- [ ] **Exercise 3:** Redesign a naive RAG system into an advanced one with caching, reranking, and evals
- [ ] **Exercise 4:** Write a system prompt from scratch for an enterprise customer support agent — cover all required sections
- [ ] **Exercise 5:** Given a production incident (hallucination in output), design the fix — guardrails, eval, prompt change

### 6.3 Study Resources for Certification
- [ ] Complete [Anthropic Courses repo](https://github.com/anthropics/courses) — all 5 courses
- [ ] Read every page of [docs.anthropic.com/en/docs](https://docs.anthropic.com/en/docs) — no skipping
- [ ] Work through [Anthropic Cookbook](https://github.com/anthropics/anthropic-cookbook) — run every notebook
- [ ] Read [Claude's model card](https://www.anthropic.com/model-card) and [usage policy](https://www.anthropic.com/legal/usage-policy)
- [ ] Study [MCP specification](https://spec.modelcontextprotocol.io) in full
- [ ] Build at least 1 MCP server independently from memory

### 6.4 Certification Flashcard Topics (Anki deck)
- [ ] All `stop_reason` values and what they mean
- [ ] All content block types (`text`, `tool_use`, `tool_result`, `image`, `document`)
- [ ] Prompt caching: TTL, which models support it, cache_control syntax
- [ ] Batch API: max requests, result retrieval, when to use
- [ ] Tool choice options: `auto`, `any`, `tool` — and when to use each
- [ ] MCP primitives: Tools vs Resources vs Prompts vs Sampling — definitions
- [ ] Extended thinking: how to enable, budget_tokens range, when it helps
- [ ] Error codes: 400, 401, 403, 404, 429, 529 — meanings and handling
- [ ] Constitutional AI: 4 stages of training (pretraining, SL-CAI, RL-CAI, RLHF)
- [ ] Hardcoded behaviors: 5 things Claude will never do regardless of instructions

---

## 🚀 PHASE 7 — Post-Certification Leverage

**Duration:** Weeks 47–56 (ongoing)
**Goal:** Capitalize on the certification for career advancement, visibility, and deeper mastery

### 7.1 Career & Visibility Actions
- [ ] Update LinkedIn with certification + 3 portfolio projects with metrics
- [ ] Write a technical blog post: "What I learned building production Claude agents"
- [ ] Speak at a local AI meetup or online webinar — 20-min talk on MCP
- [ ] Contribute to Anthropic Cookbook with a novel pattern or use case
- [ ] Open-source one of your portfolio projects with full documentation
- [ ] Apply to Anthropic's partner/developer programs if eligible

### 7.2 Advanced Topics (After Certification)
- [ ] **Claude Code** — agentic coding with `claude` CLI; building coding agents
- [ ] **Computer use** — automate browser/desktop tasks with Claude
- [ ] **Fine-tuning Claude** (if made available) — dataset preparation, evaluation
- [ ] **LLM evaluation frameworks** — deep dive into HELM, MT-Bench, custom evals
- [ ] **MLOps for agents** — versioning prompts, CI/CD for AI systems, canary deployments
- [ ] **Multimodal agents** — vision + text + tool use combined
- [ ] **Edge deployment** — running small models locally; hybrid cloud+local strategy

---

## ⚔️ PHASE 8 — DSA Daily Practice (Parallel Track from Day 1)

> This runs EVERY DAY alongside whatever phase you're in. Non-negotiable.

### Weekly DSA Schedule

| Day | Topic | Problems |
|---|---|---|
| Monday | Arrays & Hashing | 2 problems |
| Tuesday | Two Pointers / Sliding Window | 2 problems |
| Wednesday | Trees & Graphs | 2 problems |
| Thursday | Dynamic Programming | 1–2 problems |
| Friday | Stack / Queue / Linked List | 2 problems |
| Saturday | Mixed revision (revisit wrong answers) | 3 problems |
| Sunday | Contest (LeetCode Weekly) or rest | 0–4 problems |

---

## 📊 Progress Tracker

### Phase Completion

| Phase | Status | Start Date | Target End | Actual End |
|---|---|---|---|---|
| Phase 1: Python + DSA + FastAPI | ⬜ Not Started | | | |
| Phase 2: Gen AI + Claude API Mastery | ⬜ Not Started | | | |
| Phase 3: AI Agents + Tool Use + MCP | ⬜ Not Started | | | |
| Phase 4: Backend + DB + SysDesign + Prod Claude | ⬜ Not Started | | | |
| Phase 5: Production Projects + Interview | ⬜ Not Started | | | |
| Phase 6: Certification Sprint | ⬜ Not Started | | | |
| Phase 7: Post-Cert Leverage | ⬜ Not Started | | | |
| Phase 8: DSA Daily (Ongoing) | ⬜ Not Started | | | |

### Certification Domain Readiness (Self-Assessment — update weekly)

| Domain | Week 1 | Week 4 | Week 8 | Week 12 | Exam Ready? |
|---|---|---|---|---|---|
| Claude API & SDK | 0/10 | | | | |
| Prompt engineering | 2/10 | | | | |
| Tool use & function calling | 1/10 | | | | |
| Multi-agent design & MCP | 0/10 | | | | |
| Safety & Constitutional AI | 1/10 | | | | |
| Production architecture | 0/10 | | | | |

### DSA Problem Count

| Week | Mon | Tue | Wed | Thu | Fri | Sat | Sun | Total |
|---|---|---|---|---|---|---|---|---|
| Week 1 | | | | | | | | 0 |
| Week 2 | | | | | | | | 0 |
| Week 3 | | | | | | | | 0 |
| Week 4 | | | | | | | | 0 |

### Monthly Review

| Month | Key Wins | Gaps Identified | Plan Adjustments | Cert Domains Progressed |
|---|---|---|---|---|
| May 2026 | | | | |
| Jun 2026 | | | | |
| Jul 2026 | | | | |
| Aug 2026 | | | | |
| Sep 2026 | | | | |
| Oct 2026 | | | | |
| Nov 2026 | | | | |
| Dec 2026 | | | | |

---

## 🛡️ Anti-Procrastination Rules

1. **No Random Video Rule** — Only watch a video if it maps to a checkbox above. Otherwise, skip it.
2. **2-Day Rule** — Missed 2 consecutive days? Restart the current week's checklist.
3. **Sunday Review** — Every Sunday night: update this README, check boxes, write monthly review, update certification domain scores.
4. **Build > Watch** — For every 1 hour of watching, spend 2 hours coding.
5. **Festival/Vacation Protocol** — During breaks, do minimum 1 DSA problem + 30 min reading.
6. **Accountability** — Share weekly progress on LinkedIn or with a study buddy. Post Claude builds publicly.
7. **No New Tool Syndrome** — Finish current phase before exploring new frameworks/tools.
8. **Cert Domain Daily Touch** — Even on non-agent phases, spend 20 min reading one Claude doc page. Stay warm on cert material.

---

## 📚 Curated Resources

### Python
- [Python Official Docs](https://docs.python.org/3/)
- [Real Python](https://realpython.com/)
- [Fluent Python (Book)](https://www.oreilly.com/library/view/fluent-python-2nd/9781492056348/)

### DSA
- [NeetCode 150](https://neetcode.io/practice)
- [Striver's A2Z DSA Sheet](https://takeuforward.org/strivers-a2z-dsa-course/strivers-a2z-dsa-course-sheet-2)
- [LeetCode Patterns](https://seanprashad.com/leetcode-patterns/)

### Claude & Anthropic (Certification-Critical)
- [docs.anthropic.com](https://docs.anthropic.com) — PRIMARY reference for everything Claude
- [Anthropic Courses (GitHub)](https://github.com/anthropics/courses) — official 5-course curriculum
- [Anthropic Cookbook (GitHub)](https://github.com/anthropics/anthropic-cookbook) — production patterns
- [Model Context Protocol docs](https://modelcontextprotocol.io) — MCP specification & tutorials
- [Claude's model card](https://www.anthropic.com/model-card) — capabilities, safety, limitations
- [Anthropic usage policy](https://www.anthropic.com/legal/usage-policy) — what's allowed
- [Claude's Constitution](https://www.anthropic.com/research/claude-s-constitution) — values & CAI

### Gen AI & LLMs
- [LangChain Docs](https://python.langchain.com/)
- [LangGraph Docs](https://langchain-ai.github.io/langgraph/)
- [Hugging Face NLP Course](https://huggingface.co/learn/nlp-course)
- [DeepLearning.AI Short Courses](https://www.deeplearning.ai/short-courses/)
- [LLM University by Cohere](https://docs.cohere.com/docs/llmu)

### FastAPI & Backend
- [FastAPI Docs](https://fastapi.tiangolo.com/)
- [SQLAlchemy Tutorial](https://docs.sqlalchemy.org/en/20/tutorial/)
- [testdriven.io FastAPI courses](https://testdriven.io/)

### System Design
- "System Design Interview" by Alex Xu — Vol 1 & 2
- [system-design-primer (GitHub)](https://github.com/donnemartin/system-design-primer)
- [ByteByteGo YouTube](https://www.youtube.com/@ByteByteGo)

---

## 🎯 Target Companies & Roles

| Company Tier | Examples | Roles to Target |
|---|---|---|
| Tier 1 | Google, Microsoft, Amazon | SDE / ML Engineer |
| Tier 2 | Atlassian, Uber, Flipkart, Swiggy | Backend / AI Engineer |
| Tier 3 | AI Startups (well-funded) | Gen AI Engineer / AI Agent Developer |
| Tier 4 | Anthropic partners & Claude-native startups | **Claude Certified Architect** ← new target |

### What Product Companies Look For
- ✅ Strong DSA (LeetCode Medium/Hard)
- ✅ System Design (L4+ roles)
- ✅ Clean, production-grade code
- ✅ Deep understanding of tools (not just usage)
- ✅ Real projects with measurable impact
- ✅ **Claude Certified Architect credential** ← differentiator
- ❌ Framework hopping without depth
- ❌ Tutorial projects with no originality

---

## 🧭 Quick Decision Guide

```
"Should I watch this video?"
  └─ Does it map to an unchecked item above?
       ├─ YES → Watch it, take notes, check the box
       └─ NO  → Skip it. Open LeetCode or docs.anthropic.com instead.

"Should I learn this new framework?"
  └─ Is it in this roadmap?
       ├─ YES → Learn it in its scheduled phase
       └─ NO  → Add to "Future Exploration" list, don't start now

"I don't feel like studying today"
  └─ Do the MINIMUM: 1 DSA problem + 1 Claude doc page
       └─ Still don't want to? Do it anyway. Motivation follows action.

"Am I cert-ready?"
  └─ Check the Domain Readiness table above
       ├─ All domains ≥ 8/10 → Schedule the exam
       └─ Any domain < 7/10 → Two more weeks on that domain, then re-check
```

---

## 📝 Future Exploration (Park Here, Don't Start Yet)

- [ ] Kubernetes
- [ ] Terraform / IaC
- [ ] MLOps (MLflow, Kubeflow)
- [ ] Advanced fine-tuning (DPO, RLHF)
- [ ] Rust for performance-critical AI tools
- [ ] Frontend (React/Next.js) — only if needed for projects
- [ ] Claude Code deep dive (post-cert)
- [ ] Computer use automation (post-cert)

---

> _"The best time to start was yesterday. The second best time is now. But this time, follow the damn roadmap — and earn the cert that proves you did."_

**Last Updated:** May 2026
**Certification Target Date:** December 2026
