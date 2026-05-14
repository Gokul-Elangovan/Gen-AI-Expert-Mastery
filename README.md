# 🚀 Gen AI Expert & Product-Based Company Placement — Master Roadmap

> **Owner:** AI Agents Developer → aspiring Gen AI Expert & Product-Based SDE  
> **Started:** May 2026  
> **Goal:** Master Gen AI end-to-end, build production-grade projects, and crack product-based company interviews  
> **Golden Rule:** _No random YouTube marathons. Follow the phases. Check the boxes. Ship projects._

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

---

## 🗺️ Roadmap Overview (6-Month Plan)

```
Month 1-2  ▶  PHASE 1: Python Mastery + DSA Foundation + FastAPI Basics
Month 2-3  ▶  PHASE 2: Gen AI Deep Dive (LLMs, Prompt Eng, RAG, Embeddings)
Month 3-4  ▶  PHASE 3: AI Agents Mastery (LangChain, LangGraph, Tool Use, Memory)
Month 4-5  ▶  PHASE 4: Backend + Databases + System Design
Month 5-6  ▶  PHASE 5: Production-Grade Projects + Interview Prep
Ongoing    ▶  PHASE 6: DSA Daily Practice (runs parallel from Day 1)
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
- [ ] **Tracker:** Use NeetCode 150 or Striver's SDE Sheet — track in table below

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

## 🧠 PHASE 2 — Gen AI Deep Dive

**Duration:** Weeks 9–14  
**Goal:** Understand LLMs from the ground up, build RAG systems, master prompt engineering

### 2.1 LLM Fundamentals
- [ ] How Transformers work — attention mechanism, tokenization
- [ ] GPT architecture — decoder-only, autoregressive generation
- [ ] Token limits, temperature, top-p, frequency penalty — experiment hands-on
- [ ] Embedding models — what they are, when to use them
- [ ] OpenAI API / Anthropic API / Google Gemini API — direct usage (no framework)
- [ ] Streaming responses — implement in Python
- [ ] **Mini-Project:** Direct API chatbot with streaming, multi-turn conversation

### 2.2 Prompt Engineering Mastery
- [ ] Zero-shot, few-shot, chain-of-thought prompting
- [ ] System prompts — structuring behavior
- [ ] Output formatting — JSON mode, structured outputs
- [ ] Prompt chaining — breaking complex tasks into steps
- [ ] Guardrails & safety — input validation, output filtering
- [ ] **Mini-Project:** Automated resume analyzer using prompt chaining

### 2.3 RAG (Retrieval-Augmented Generation)
- [ ] What is RAG — architecture overview
- [ ] Document loaders — PDF, web, markdown, CSV
- [ ] Text splitting strategies — chunk size, overlap, semantic chunking
- [ ] Vector databases — ChromaDB, Pinecone, Weaviate (pick 2)
- [ ] Embedding + similarity search — cosine similarity, MMR
- [ ] RAG pipeline — query → retrieve → augment → generate
- [ ] Advanced RAG — re-ranking, hybrid search, query transformation
- [ ] Evaluation — faithfulness, relevancy, RAGAS framework
- [ ] **Project:** Q&A system over your own documents (PDF/Notion)

### 2.4 Fine-Tuning Basics
- [ ] When to fine-tune vs when to use RAG
- [ ] LoRA & QLoRA concepts
- [ ] Fine-tune a small model on custom dataset (Hugging Face)
- [ ] Evaluate fine-tuned model vs base model

---

## 🤖 PHASE 3 — AI Agents Mastery (LangChain + LangGraph)

**Duration:** Weeks 15–20  
**Goal:** Build production-quality AI agents from scratch, understand every component deeply

### 3.1 LangChain Deep Dive
- [ ] LangChain Expression Language (LCEL) — pipes, runnables, chains
- [ ] Chat models — structured outputs, tool calling
- [ ] Output parsers — Pydantic, JSON, CSV
- [ ] Prompt templates — ChatPromptTemplate, MessagesPlaceholder
- [ ] Document loaders & text splitters (revisit with depth)
- [ ] Retrievers — vector store, multi-query, ensemble
- [ ] Memory — ConversationBufferMemory, Summary, Entity
- [ ] Callbacks & tracing — LangSmith integration
- [ ] **Project:** Multi-document chatbot with memory & citations

### 3.2 LangGraph — Stateful Agent Workflows
- [ ] Graph concepts — nodes, edges, conditional edges, state
- [ ] StateGraph — define and compile
- [ ] Human-in-the-loop patterns
- [ ] Branching & parallel execution
- [ ] Persistence & checkpointing
- [ ] Multi-agent architectures — supervisor, hierarchical
- [ ] Tool integration — custom tools, API tools
- [ ] Error handling & retry in graphs
- [ ] **Project:** Multi-agent research assistant (planner → researcher → writer → reviewer)

### 3.3 Building Agents from Scratch (No Framework)
- [ ] ReAct pattern — implement manually with raw API calls
- [ ] Tool-use loop — parse LLM output → call tool → feed back
- [ ] Planning & reflection agents
- [ ] **Why this matters:** Product companies test fundamentals, not framework knowledge

---

## 🏗️ PHASE 4 — Backend + Databases + System Design

**Duration:** Weeks 21–26  
**Goal:** Build production-grade backends, understand databases deeply, learn system design patterns

### 4.1 FastAPI Advanced
- [ ] Authentication — JWT, OAuth2 with FastAPI
- [ ] Database integration — SQLAlchemy ORM + Alembic migrations
- [ ] Async database queries — asyncpg, databases library
- [ ] File uploads & storage (S3-compatible)
- [ ] WebSocket support — real-time chat
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
- [ ] **Project:** Design and implement DB schema for an AI chatbot platform

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

---

## 🚢 PHASE 5 — Production-Grade Projects + Interview Prep

**Duration:** Weeks 27–32  
**Goal:** Ship 2-3 portfolio-worthy projects, drill interviews

### 5.1 Production Skills
- [ ] Docker — containerize your apps
- [ ] Docker Compose — multi-service setup (app + db + redis)
- [ ] CI/CD — GitHub Actions pipeline
- [ ] Logging & monitoring — structured logging, basic observability
- [ ] Error tracking — Sentry integration
- [ ] Environment management — .env, secrets management
- [ ] Cloud deployment — AWS (EC2, S3, RDS) or GCP basics
- [ ] Cost optimization for LLM applications

### 5.2 Portfolio Projects (Build & Deploy These)

#### 🏆 Project 1: AI-Powered Document Intelligence Platform
- [ ] Multi-format document ingestion (PDF, DOCX, web)
- [ ] Advanced RAG with hybrid search & re-ranking
- [ ] FastAPI backend with auth & rate limiting
- [ ] PostgreSQL + ChromaDB/Pinecone
- [ ] Streaming responses with WebSocket
- [ ] Docker + cloud deployment
- [ ] LangSmith tracing in production

#### 🏆 Project 2: Multi-Agent Workflow Engine
- [ ] LangGraph-based agent orchestration
- [ ] Multiple specialized agents (research, coding, analysis)
- [ ] Human-in-the-loop approval steps
- [ ] Persistent state & conversation history
- [ ] FastAPI backend + real-time updates
- [ ] Production monitoring & error handling

#### 🏆 Project 3: Personal AI Assistant API
- [ ] Tool-calling agent with 10+ tools (web search, email, calendar, code exec)
- [ ] Memory & personalization layer
- [ ] Rate-limited public API
- [ ] Usage analytics dashboard
- [ ] Comprehensive test suite

### 5.3 Interview Preparation
- [ ] DSA — reach 200+ LeetCode problems (medium focus)
- [ ] System Design — practice 10 designs with timer (45 min each)
- [ ] Machine Learning basics — regression, classification, evaluation metrics
- [ ] Gen AI concepts — prepare 20 common interview questions
- [ ] Behavioral — STAR method, prepare 10 stories
- [ ] Resume — highlight projects with metrics & impact
- [ ] Mock interviews — schedule 2 per week

---

## ⚔️ PHASE 6 — DSA Daily Practice (Parallel Track from Day 1)

> This runs EVERY DAY alongside whatever phase you're in. Non-negotiable.

### Weekly DSA Schedule

| Day | Topic | Problems |
|---|---|---|
| Monday | Arrays & Hashing | 2 problems |
| Tuesday | Two Pointers / Sliding Window | 2 problems |
| Wednesday | Trees & Graphs | 2 problems |
| Thursday | Dynamic Programming | 1-2 problems |
| Friday | Stack / Queue / Linked List | 2 problems |
| Saturday | Mixed revision (revisit wrong answers) | 3 problems |
| Sunday | Contest (LeetCode Weekly) or rest | 0-4 problems |

---

## 📊 Progress Tracker

### Phase Completion

| Phase | Status | Start Date | Target End | Actual End |
|---|---|---|---|---|
| Phase 1: Python + DSA + FastAPI | ⬜ Not Started | | | |
| Phase 2: Gen AI Deep Dive | ⬜ Not Started | | | |
| Phase 3: AI Agents Mastery | ⬜ Not Started | | | |
| Phase 4: Backend + DB + SysDesign | ⬜ Not Started | | | |
| Phase 5: Production + Interview | ⬜ Not Started | | | |
| Phase 6: DSA Daily (Ongoing) | ⬜ Not Started | | | |

### DSA Problem Count

| Week | Mon | Tue | Wed | Thu | Fri | Sat | Sun | Total |
|---|---|---|---|---|---|---|---|---|
| Week 1 | | | | | | | | 0 |
| Week 2 | | | | | | | | 0 |
| Week 3 | | | | | | | | 0 |
| Week 4 | | | | | | | | 0 |

### Monthly Review

| Month | Key Wins | Gaps Identified | Plan Adjustments |
|---|---|---|---|
| May 2026 | | | |
| Jun 2026 | | | |
| Jul 2026 | | | |
| Aug 2026 | | | |
| Sep 2026 | | | |
| Oct 2026 | | | |

---

## 🛡️ Anti-Procrastination Rules

1. **No Random Video Rule** — Only watch a video if it maps to a checkbox above. Otherwise, skip it.
2. **2-Day Rule** — Missed 2 consecutive days? Restart the current week's checklist.
3. **Sunday Review** — Every Sunday night: update this README, check boxes, write monthly review.
4. **Build > Watch** — For every 1 hour of watching, spend 2 hours coding.
5. **Festival/Vacation Protocol** — During breaks, do minimum 1 DSA problem + 30 min reading. Zero days = zero progress.
6. **Accountability** — Share weekly progress on LinkedIn or with a study buddy.
7. **No New Tool Syndrome** — Finish current phase before exploring new frameworks/tools.

---

## 📚 Curated Resources (Don't Google Random Stuff)

### Python
- [Python Official Docs](https://docs.python.org/3/) — always the first source
- [Real Python](https://realpython.com/) — for advanced topics
- [Fluent Python (Book)](https://www.oreilly.com/library/view/fluent-python-2nd/9781492056348/) — deep mastery

### DSA
- [NeetCode 150](https://neetcode.io/practice) — structured problem list
- [Striver's A2Z DSA Sheet](https://takeuforward.org/strivers-a2z-dsa-course/strivers-a2z-dsa-course-sheet-2) — comprehensive
- [LeetCode Patterns](https://seanprashad.com/leetcode-patterns/) — pattern-based approach

### Gen AI & LLMs
- [LangChain Docs](https://python.langchain.com/) — official documentation
- [LangGraph Docs](https://langchain-ai.github.io/langgraph/) — agent workflows
- [Hugging Face NLP Course](https://huggingface.co/learn/nlp-course) — transformer fundamentals
- [DeepLearning.AI Short Courses](https://www.deeplearning.ai/short-courses/) — Andrew Ng's bite-sized courses
- [LLM University by Cohere](https://docs.cohere.com/docs/llmu) — LLM fundamentals

### FastAPI & Backend
- [FastAPI Docs](https://fastapi.tiangolo.com/) — best-in-class documentation
- [SQLAlchemy Tutorial](https://docs.sqlalchemy.org/en/20/tutorial/) — ORM mastery
- [testdriven.io FastAPI courses](https://testdriven.io/) — production patterns

### System Design
- "System Design Interview" by Alex Xu — Vol 1 & 2
- [system-design-primer (GitHub)](https://github.com/donnemartin/system-design-primer)
- [ByteByteGo YouTube](https://www.youtube.com/@ByteByteGo) — visual system design

---

## 🎯 Target Companies & Roles

| Company Tier | Examples | Roles to Target |
|---|---|---|
| Tier 1 | Google, Microsoft, Amazon | SDE / ML Engineer |
| Tier 2 | Atlassian, Uber, Flipkart, Swiggy | Backend / AI Engineer |
| Tier 3 | AI Startups (well-funded) | Gen AI Engineer / AI Agent Developer |
| Tier 3 | Product Companies | Full Stack / Backend with AI |

### What Product Companies Look For
- ✅ Strong DSA (LeetCode Medium/Hard)
- ✅ System Design (L4+ roles)
- ✅ Clean, production-grade code
- ✅ Deep understanding of tools (not just usage)
- ✅ Real projects with measurable impact
- ❌ Framework hopping without depth
- ❌ Tutorial projects with no originality

---

## 🧭 Quick Decision Guide

```
"Should I watch this video?"
  └─ Does it map to an unchecked item above? 
       ├─ YES → Watch it, take notes, check the box
       └─ NO  → Skip it. Open LeetCode instead.

"Should I learn this new framework?"
  └─ Is it in this roadmap?
       ├─ YES → Learn it in its scheduled phase
       └─ NO  → Add to "Future Exploration" list, don't start now

"I don't feel like studying today"
  └─ Do the MINIMUM: 1 DSA problem + 30 min reading
       └─ Still don't want to? Do it anyway. Motivation follows action.
```

---

## 📝 Future Exploration (Park Here, Don't Start Yet)

- [ ] Kubernetes
- [ ] Terraform / IaC
- [ ] MLOps (MLflow, Kubeflow)
- [ ] Advanced fine-tuning (DPO, RLHF)
- [ ] Rust for performance-critical AI tools
- [ ] Frontend (React/Next.js) — only if needed for projects

---

> _"The best time to start was yesterday. The second best time is now. But this time, follow the damn roadmap."_

**Last Updated:** May 14, 2026
