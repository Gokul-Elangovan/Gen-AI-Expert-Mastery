# 🤖 Claude API → Multi-Agent AI Developer Roadmap
### From Tool Calls to Production-Grade Multi-Agent Systems (3–4 Months)

> **Your Starting Point:** You know tool calls with the Anthropic SDK  
> **Your Goal:** Build and ship multi-agent AI applications  
> **Budget:** $5 API credits (carefully managed with tips below)  
> **Timeline:** 3–4 months | ~10–15 hrs/week

---

## 📊 Progress Tracker

| Phase | Topic | Status | Project |
|-------|-------|--------|---------|
| Phase 1 | Core API Mastery | ⬜ Not Started | Smart Research Assistant |
| Phase 2 | Advanced Tool Use & Memory | ⬜ Not Started | Personal AI Knowledge Base |
| Phase 3 | Orchestration Patterns | ⬜ Not Started | Multi-Step Workflow Engine |
| Phase 4 | Multi-Agent Systems | ⬜ Not Started | Agent Swarm App |
| Phase 5 | Production & Deployment | ⬜ Not Started | SaaS-Ready AI Product |

> Update status: ⬜ Not Started → 🔄 In Progress → ✅ Done

---

## 💰 Credit Management Strategy ($5 Budget)

Your $5 gives you roughly **5M input tokens or 500K output tokens** on Haiku (cheapest).

| Model | Input Cost | Output Cost | Use When |
|-------|-----------|-------------|----------|
| `claude-haiku-4-5` | ~$0.25/M | ~$1.25/M | Learning, testing, bulk tasks |
| `claude-sonnet-4-5` | ~$3/M | ~$15/M | Final projects, demos |
| `claude-opus-4-5` | ~$15/M | ~$75/M | Avoid during learning phase |

**Tips to stretch your $5:**
- 🏷️ Always use `claude-haiku-4-5-20251001` while learning
- 📏 Set `max_tokens: 300–500` during experiments
- 🗃️ Cache system prompts using `cache_control` (up to 90% savings)
- 🧪 Mock API responses in unit tests — only call real API for integration tests
- 📋 Use `anthropic.messages.count_tokens()` to check cost before calling
- 📦 Batch test with Batch API (50% discount, async)

---

## 🗺️ PHASE 1 — Core API Mastery (Weeks 1–3)

> **Goal:** Master every messaging primitive before building agents

### Week 1 — Messages, Streaming & Prompt Engineering

#### Concepts to Learn
- [ ] Message structure (system, user, assistant roles)
- [ ] Streaming responses with `stream=True`
- [ ] Token counting and cost estimation
- [ ] Prompt caching with `cache_control`
- [ ] Temperature, top_p, top_k tuning
- [ ] Stop sequences

#### Code Exercises

**Exercise 1.1 — Streaming with token tracking**
```python
import anthropic

client = anthropic.Anthropic()

def stream_with_cost(prompt: str, system: str = "You are helpful."):
    input_tokens = 0
    output_tokens = 0
    
    with client.messages.stream(
        model="claude-haiku-4-5-20251001",
        max_tokens=500,
        system=system,
        messages=[{"role": "user", "content": prompt}]
    ) as stream:
        for text in stream.text_stream:
            print(text, end="", flush=True)
        
        # Get final message for token counts
        final = stream.get_final_message()
        input_tokens = final.usage.input_tokens
        output_tokens = final.usage.output_tokens
    
    cost = (input_tokens * 0.00000025) + (output_tokens * 0.00000125)
    print(f"\n\n💰 Cost: ${cost:.6f} | In: {input_tokens} | Out: {output_tokens}")

stream_with_cost("Explain Python decorators in 3 sentences.")
```

**Exercise 1.2 — Prompt Caching (saves 90% on repeated system prompts)**
```python
# Cache a large system prompt to save tokens on repeated calls
large_system = "You are an expert Python developer..." + "..." * 500  # large context

response = client.messages.create(
    model="claude-haiku-4-5-20251001",
    max_tokens=300,
    system=[
        {
            "type": "text",
            "text": large_system,
            "cache_control": {"type": "ephemeral"}  # Cache this!
        }
    ],
    messages=[{"role": "user", "content": "How do I use asyncio?"}]
)
print(f"Cache write tokens: {response.usage.cache_creation_input_tokens}")
print(f"Cache read tokens: {response.usage.cache_read_input_tokens}")
```

**Exercise 1.3 — Multi-turn conversation manager**
```python
class ConversationManager:
    def __init__(self, system: str, model: str = "claude-haiku-4-5-20251001"):
        self.client = anthropic.Anthropic()
        self.system = system
        self.model = model
        self.history = []
        self.total_cost = 0.0
    
    def chat(self, user_message: str) -> str:
        self.history.append({"role": "user", "content": user_message})
        
        response = self.client.messages.create(
            model=self.model,
            max_tokens=500,
            system=self.system,
            messages=self.history
        )
        
        assistant_msg = response.content[0].text
        self.history.append({"role": "assistant", "content": assistant_msg})
        
        # Track cost
        cost = (response.usage.input_tokens * 0.00000025) + \
               (response.usage.output_tokens * 0.00000125)
        self.total_cost += cost
        
        return assistant_msg
    
    def reset(self):
        self.history = []
```

---

### Week 2 — Advanced Tool Use (You Know Basics — Go Deeper)

#### Concepts to Learn
- [ ] Parallel tool calls (multiple tools in one turn)
- [ ] Tool use in multi-turn conversations
- [ ] Error handling in tool responses
- [ ] Forced tool use with `tool_choice`
- [ ] Complex tool schemas with nested objects
- [ ] Tool result formatting best practices

#### Code Exercises

**Exercise 2.1 — Parallel tool execution**
```python
import json
import concurrent.futures
from typing import Any

tools = [
    {
        "name": "get_weather",
        "description": "Get weather for a city",
        "input_schema": {
            "type": "object",
            "properties": {
                "city": {"type": "string"},
                "unit": {"type": "string", "enum": ["celsius", "fahrenheit"]}
            },
            "required": ["city"]
        }
    },
    {
        "name": "get_news",
        "description": "Get latest news headlines for a topic",
        "input_schema": {
            "type": "object",
            "properties": {
                "topic": {"type": "string"},
                "count": {"type": "integer", "default": 3}
            },
            "required": ["topic"]
        }
    }
]

def execute_tool(tool_name: str, tool_input: dict) -> Any:
    """Your actual tool implementations go here"""
    if tool_name == "get_weather":
        return {"temp": 22, "condition": "sunny", "city": tool_input["city"]}
    elif tool_name == "get_news":
        return {"headlines": [f"News about {tool_input['topic']} #{i}" 
                              for i in range(tool_input.get("count", 3))]}

def run_agent_loop(user_message: str):
    messages = [{"role": "user", "content": user_message}]
    
    while True:
        response = client.messages.create(
            model="claude-haiku-4-5-20251001",
            max_tokens=1000,
            tools=tools,
            messages=messages
        )
        
        # No tool calls — final answer
        if response.stop_reason == "end_turn":
            return response.content[0].text
        
        # Process ALL tool calls (possibly parallel)
        tool_results = []
        tool_calls = [b for b in response.content if b.type == "tool_use"]
        
        # Execute tools in parallel
        with concurrent.futures.ThreadPoolExecutor() as executor:
            futures = {
                executor.submit(execute_tool, tc.name, tc.input): tc
                for tc in tool_calls
            }
            for future, tool_call in futures.items():
                result = future.result()
                tool_results.append({
                    "type": "tool_result",
                    "tool_use_id": tool_call.id,
                    "content": json.dumps(result)
                })
        
        # Continue conversation with tool results
        messages.append({"role": "assistant", "content": response.content})
        messages.append({"role": "user", "content": tool_results})
```

**Exercise 2.2 — Forced structured output via tool use**
```python
# Use tool_choice to force Claude to always return structured data
extraction_tool = {
    "name": "extract_entities",
    "description": "Extract entities from text",
    "input_schema": {
        "type": "object",
        "properties": {
            "people": {"type": "array", "items": {"type": "string"}},
            "organizations": {"type": "array", "items": {"type": "string"}},
            "locations": {"type": "array", "items": {"type": "string"}},
            "dates": {"type": "array", "items": {"type": "string"}}
        },
        "required": ["people", "organizations", "locations", "dates"]
    }
}

def extract_entities(text: str) -> dict:
    response = client.messages.create(
        model="claude-haiku-4-5-20251001",
        max_tokens=500,
        tools=[extraction_tool],
        tool_choice={"type": "tool", "name": "extract_entities"},  # Force it!
        messages=[{"role": "user", "content": f"Extract entities from: {text}"}]
    )
    return response.content[0].input  # Always a tool call now
```

---

### Week 3 — Vision, Documents & Batch API

#### Concepts to Learn
- [ ] Image input (base64 + URL)
- [ ] PDF/document processing
- [ ] Message Batches API (async, 50% cheaper)
- [ ] Counting tokens before calling
- [ ] Model selection strategy

#### Code Exercises

**Exercise 3.1 — Batch processing (50% cost savings)**
```python
# Batch API — process many requests async, 50% cheaper
import time

def process_batch(prompts: list[str]) -> list[str]:
    # Create batch
    requests = [
        {
            "custom_id": f"req-{i}",
            "params": {
                "model": "claude-haiku-4-5-20251001",
                "max_tokens": 200,
                "messages": [{"role": "user", "content": p}]
            }
        }
        for i, p in enumerate(prompts)
    ]
    
    batch = client.messages.batches.create(requests=requests)
    print(f"Batch created: {batch.id}")
    
    # Poll until done
    while True:
        batch = client.messages.batches.retrieve(batch.id)
        print(f"Status: {batch.processing_status}")
        if batch.processing_status == "ended":
            break
        time.sleep(10)
    
    # Collect results
    results = {}
    for result in client.messages.batches.results(batch.id):
        if result.result.type == "succeeded":
            results[result.custom_id] = result.result.message.content[0].text
    
    return [results[f"req-{i}"] for i in range(len(prompts))]
```

### 🏗️ Phase 1 Project: Smart Research Assistant

**What you'll build:** A CLI research assistant that takes a topic, searches for information using tools, summarizes findings, and saves results to a file.

**Features:**
- Multi-turn conversation with memory
- 3+ tools (web search mock, calculator, file writer)
- Streaming output
- Cost tracking dashboard
- Conversation export to JSON

**File structure:**
```
research_assistant/
├── main.py              # CLI entry point
├── agent.py             # Core agent loop
├── tools/
│   ├── __init__.py
│   ├── search.py        # Mock web search tool
│   ├── calculator.py    # Math tool
│   └── file_writer.py   # Save results tool
├── memory.py            # Conversation history
└── config.py            # Model & cost config
```

---

## 🗺️ PHASE 2 — Memory, Context & Knowledge (Weeks 4–6)

> **Goal:** Give your agents persistent memory and long-context capabilities

### Week 4 — Memory Architectures

#### Concepts to Learn
- [ ] Short-term memory (conversation history)
- [ ] Long-term memory (vector stores / SQLite)
- [ ] Episodic memory (past interactions)
- [ ] Semantic memory (facts/knowledge)
- [ ] Memory summarization (compress old history)
- [ ] Context window management

#### Memory Architecture Patterns

```
┌─────────────────────────────────────────────────────┐
│                   MEMORY LAYERS                      │
├──────────────┬──────────────────┬───────────────────┤
│  In-Context  │   External Store  │   Compressed      │
│  (last 10   │   (SQLite/Vector) │   (Summarized     │
│   messages) │   (facts, docs)   │    old history)   │
└──────────────┴──────────────────┴───────────────────┘
```

**Exercise 4.1 — Memory with automatic summarization**
```python
import sqlite3
import json
from datetime import datetime

class AgentMemory:
    def __init__(self, db_path: str = "agent_memory.db"):
        self.conn = sqlite3.connect(db_path)
        self.setup_db()
        self.short_term = []  # In-context messages
        self.max_short_term = 10
    
    def setup_db(self):
        self.conn.execute("""
            CREATE TABLE IF NOT EXISTS memories (
                id INTEGER PRIMARY KEY,
                type TEXT,  -- 'fact', 'summary', 'preference'
                content TEXT,
                created_at TIMESTAMP,
                importance REAL DEFAULT 0.5
            )
        """)
        self.conn.commit()
    
    def add_message(self, role: str, content: str):
        self.short_term.append({"role": role, "content": content})
        
        # Auto-summarize when too long
        if len(self.short_term) > self.max_short_term:
            self._summarize_and_compress()
    
    def _summarize_and_compress(self):
        """Summarize old messages and store in long-term memory"""
        old_messages = self.short_term[:-4]  # Keep last 4 fresh
        
        summary_response = client.messages.create(
            model="claude-haiku-4-5-20251001",
            max_tokens=300,
            messages=[{
                "role": "user",
                "content": f"Summarize key points from this conversation:\n{json.dumps(old_messages)}"
            }]
        )
        
        summary = summary_response.content[0].text
        self.store_fact(summary, "summary")
        self.short_term = self.short_term[-4:]  # Keep only recent
    
    def store_fact(self, fact: str, fact_type: str = "fact", importance: float = 0.5):
        self.conn.execute(
            "INSERT INTO memories (type, content, created_at, importance) VALUES (?, ?, ?, ?)",
            (fact_type, fact, datetime.now(), importance)
        )
        self.conn.commit()
    
    def retrieve_relevant(self, query: str, limit: int = 5) -> list[str]:
        """Simple keyword search (upgrade to vector search later)"""
        cursor = self.conn.execute(
            "SELECT content FROM memories ORDER BY importance DESC, created_at DESC LIMIT ?",
            (limit,)
        )
        return [row[0] for row in cursor.fetchall()]
    
    def build_context(self, current_query: str) -> list[dict]:
        """Build full context: memories + recent history"""
        relevant = self.retrieve_relevant(current_query)
        
        if relevant:
            memory_context = "Relevant memories:\n" + "\n".join(f"- {m}" for m in relevant)
            messages = [{"role": "user", "content": memory_context},
                       {"role": "assistant", "content": "I've noted the context."}]
        else:
            messages = []
        
        return messages + self.short_term
```

---

### Week 5 — RAG (Retrieval-Augmented Generation)

#### Concepts to Learn
- [ ] Chunking strategies (fixed, semantic, recursive)
- [ ] Embeddings basics (conceptual)
- [ ] Simple keyword/BM25 search
- [ ] Context stuffing vs retrieval
- [ ] Re-ranking results
- [ ] Citation and grounding

**Exercise 5.1 — Simple RAG pipeline (no vector DB needed)**
```python
import re
from collections import Counter

class SimpleRAG:
    """RAG without a vector database — keyword + TF-IDF search"""
    
    def __init__(self):
        self.chunks = []
        self.client = anthropic.Anthropic()
    
    def ingest(self, text: str, chunk_size: int = 500):
        """Split text into overlapping chunks"""
        words = text.split()
        for i in range(0, len(words), chunk_size - 50):  # 50-word overlap
            chunk = " ".join(words[i:i + chunk_size])
            self.chunks.append({
                "text": chunk,
                "id": len(self.chunks),
                "words": Counter(chunk.lower().split())
            })
    
    def search(self, query: str, top_k: int = 3) -> list[str]:
        """BM25-style keyword search"""
        query_words = set(query.lower().split())
        scores = []
        
        for chunk in self.chunks:
            score = sum(chunk["words"].get(w, 0) for w in query_words)
            scores.append((score, chunk["text"]))
        
        scores.sort(reverse=True)
        return [text for _, text in scores[:top_k] if _ > 0]
    
    def answer(self, question: str) -> str:
        context_chunks = self.search(question)
        
        if not context_chunks:
            context = "No relevant context found."
        else:
            context = "\n\n---\n\n".join(context_chunks)
        
        response = self.client.messages.create(
            model="claude-haiku-4-5-20251001",
            max_tokens=500,
            system="Answer questions using ONLY the provided context. "
                   "If the answer isn't in the context, say so.",
            messages=[{
                "role": "user",
                "content": f"Context:\n{context}\n\nQuestion: {question}"
            }]
        )
        return response.content[0].text
```

---

### Week 6 — Extended Thinking

#### Concepts to Learn
- [ ] When to use extended thinking
- [ ] Streaming thinking blocks
- [ ] Thinking budget control
- [ ] Interleaved thinking
- [ ] Cost/quality tradeoffs

**Exercise 6.1 — Extended thinking for complex reasoning**
```python
def solve_complex_problem(problem: str, budget_tokens: int = 5000) -> dict:
    """Use extended thinking for problems requiring deep reasoning"""
    
    response = client.messages.create(
        model="claude-sonnet-4-5",  # Thinking requires Sonnet+
        max_tokens=8000,
        thinking={
            "type": "enabled",
            "budget_tokens": budget_tokens  # Control thinking depth
        },
        messages=[{"role": "user", "content": problem}]
    )
    
    thinking_text = ""
    answer_text = ""
    
    for block in response.content:
        if block.type == "thinking":
            thinking_text = block.thinking
        elif block.type == "text":
            answer_text = block.text
    
    return {
        "thinking": thinking_text,
        "answer": answer_text,
        "thinking_tokens": len(thinking_text.split()),
        "cost_estimate": response.usage.input_tokens * 0.000003
    }

# Use for: math problems, logic puzzles, code debugging, strategy
result = solve_complex_problem("Design a caching strategy for a high-traffic API with 10M req/day")
```

### 🏗️ Phase 2 Project: Personal AI Knowledge Base

**What you'll build:** An AI that remembers everything you tell it, learns from documents you feed it, and answers questions with citations.

**Features:**
- Ingest PDFs, text files, URLs
- Persistent SQLite memory
- RAG-powered Q&A with source citations
- Conversation history with auto-summarization
- "What do I know about X?" queries
- Export knowledge graph

**File structure:**
```
knowledge_base/
├── main.py
├── ingestor.py        # PDF/text/URL ingestion
├── rag.py             # Retrieval pipeline
├── memory.py          # Persistent memory
├── agent.py           # Q&A agent with citations
└── knowledge.db       # SQLite database
```

---

## 🗺️ PHASE 3 — Orchestration Patterns (Weeks 7–9)

> **Goal:** Chain Claude calls into reliable multi-step workflows

### Week 7 — Prompt Chaining & Pipelines

#### Concepts to Learn
- [ ] Sequential chaining (output → next input)
- [ ] Conditional branching
- [ ] Validation loops (retry on bad output)
- [ ] Map-reduce patterns
- [ ] Fan-out / Fan-in
- [ ] Error recovery strategies

#### Orchestration Patterns

**Pattern 1: Sequential Pipeline**
```python
class Pipeline:
    def __init__(self):
        self.client = anthropic.Anthropic()
        self.steps = []
    
    def add_step(self, name: str, system_prompt: str, transform=None):
        self.steps.append({
            "name": name,
            "system": system_prompt,
            "transform": transform or (lambda x: x)
        })
        return self  # Enable chaining
    
    def run(self, initial_input: str, verbose: bool = True) -> dict:
        current = initial_input
        results = {"input": initial_input, "steps": []}
        
        for step in self.steps:
            if verbose:
                print(f"\n🔄 Step: {step['name']}")
            
            response = self.client.messages.create(
                model="claude-haiku-4-5-20251001",
                max_tokens=1000,
                system=step["system"],
                messages=[{"role": "user", "content": current}]
            )
            
            output = response.content[0].text
            output = step["transform"](output)  # Optional transform
            
            results["steps"].append({
                "name": step["name"],
                "input": current,
                "output": output
            })
            
            current = output
        
        results["final_output"] = current
        return results

# Usage example: Blog post pipeline
pipeline = (Pipeline()
    .add_step("outline", "Create a structured outline for this topic. Return as numbered list.")
    .add_step("expand", "Expand this outline into a full blog post with headers and paragraphs.")
    .add_step("edit", "Edit for clarity, fix grammar, improve flow. Return polished version.")
    .add_step("seo", "Add SEO meta description and suggest 5 keywords. Keep article intact."))

result = pipeline.run("The future of AI agents in software development")
```

**Pattern 2: Validation Loop**
```python
import json

def validated_json_output(prompt: str, schema_description: str, max_retries: int = 3) -> dict:
    """Keep retrying until we get valid JSON"""
    
    system = f"""Return ONLY valid JSON matching this schema:
{schema_description}
No markdown, no explanation, just raw JSON."""
    
    for attempt in range(max_retries):
        response = client.messages.create(
            model="claude-haiku-4-5-20251001",
            max_tokens=500,
            system=system,
            messages=[{"role": "user", "content": prompt}]
        )
        
        try:
            # Strip any markdown fences
            text = response.content[0].text.strip()
            text = re.sub(r'^```json\n?|\n?```$', '', text)
            return json.loads(text)
        except json.JSONDecodeError as e:
            if attempt == max_retries - 1:
                raise ValueError(f"Failed to get valid JSON after {max_retries} attempts")
            # Add error context for next attempt
            prompt = f"Previous output had JSON error: {e}\nTry again: {prompt}"
    
    return {}

**Pattern 3: Map-Reduce**
```python
def map_reduce(documents: list[str], question: str) -> str:
    """Process many documents in parallel, then synthesize"""
    
    # MAP: Summarize each document
    with concurrent.futures.ThreadPoolExecutor(max_workers=5) as executor:
        def summarize(doc):
            r = client.messages.create(
                model="claude-haiku-4-5-20251001",
                max_tokens=200,
                messages=[{"role": "user", 
                          "content": f"Extract key facts relevant to '{question}':\n{doc}"}]
            )
            return r.content[0].text
        
        summaries = list(executor.map(summarize, documents))
    
    # REDUCE: Synthesize all summaries
    combined = "\n\n".join(f"[Doc {i+1}]: {s}" for i, s in enumerate(summaries))
    
    final = client.messages.create(
        model="claude-haiku-4-5-20251001",
        max_tokens=500,
        messages=[{
            "role": "user",
            "content": f"Based on these summaries, answer: {question}\n\n{combined}"
        }]
    )
    return final.content[0].text
```

---

### Week 8 — Routing & Specialization

#### Concepts to Learn
- [ ] Classifier-router pattern
- [ ] Specialized sub-agents
- [ ] Dynamic tool selection
- [ ] Agent handoffs
- [ ] Quality gates

**Exercise 8.1 — Intent Router**
```python
INTENT_ROUTING = {
    "code": "You are a senior software engineer. Help with code.",
    "math": "You are a mathematics expert. Solve step by step.",
    "creative": "You are a creative writer. Be imaginative and engaging.",
    "research": "You are a research analyst. Be thorough and cite reasoning.",
    "general": "You are a helpful assistant."
}

def route_to_specialist(user_message: str) -> str:
    # Step 1: Classify intent
    classifier_response = client.messages.create(
        model="claude-haiku-4-5-20251001",
        max_tokens=10,
        system=f"Classify the intent. Reply with ONE word from: {list(INTENT_ROUTING.keys())}",
        messages=[{"role": "user", "content": user_message}]
    )
    
    intent = classifier_response.content[0].text.strip().lower()
    system_prompt = INTENT_ROUTING.get(intent, INTENT_ROUTING["general"])
    
    print(f"🎯 Routed to: {intent}")
    
    # Step 2: Answer with specialist
    response = client.messages.create(
        model="claude-haiku-4-5-20251001",
        max_tokens=800,
        system=system_prompt,
        messages=[{"role": "user", "content": user_message}]
    )
    
    return response.content[0].text
```

---

### Week 9 — State Machines & Complex Workflows

#### Concepts to Learn
- [ ] Finite state machine agents
- [ ] Async agent loops
- [ ] Checkpointing and resumability
- [ ] Human-in-the-loop patterns
- [ ] Approval gates

**Exercise 9.1 — Stateful Agent with checkpointing**
```python
import json
import os
from enum import Enum
from dataclasses import dataclass, asdict

class AgentState(Enum):
    IDLE = "idle"
    PLANNING = "planning"
    EXECUTING = "executing"
    REVIEWING = "reviewing"
    WAITING_APPROVAL = "waiting_approval"
    DONE = "done"
    ERROR = "error"

@dataclass
class AgentContext:
    state: str
    task: str
    plan: list
    completed_steps: list
    current_step: int
    results: dict
    
    def save(self, path: str):
        with open(path, "w") as f:
            json.dump(asdict(self), f, indent=2)
    
    @classmethod
    def load(cls, path: str):
        with open(path) as f:
            return cls(**json.load(f))

class StatefulAgent:
    def __init__(self, checkpoint_path: str = "agent_checkpoint.json"):
        self.client = anthropic.Anthropic()
        self.checkpoint_path = checkpoint_path
    
    def run(self, task: str, require_approval: bool = True):
        # Resume from checkpoint if exists
        if os.path.exists(self.checkpoint_path):
            ctx = AgentContext.load(self.checkpoint_path)
            print(f"♻️ Resuming from: {ctx.state}")
        else:
            ctx = AgentContext(
                state=AgentState.PLANNING.value,
                task=task, plan=[], completed_steps=[],
                current_step=0, results={}
            )
        
        while ctx.state != AgentState.DONE.value:
            if ctx.state == AgentState.PLANNING.value:
                ctx = self._plan(ctx)
            elif ctx.state == AgentState.WAITING_APPROVAL.value:
                ctx = self._get_approval(ctx, require_approval)
            elif ctx.state == AgentState.EXECUTING.value:
                ctx = self._execute_step(ctx)
            elif ctx.state == AgentState.REVIEWING.value:
                ctx = self._review(ctx)
            
            # Checkpoint after each state transition
            ctx.save(self.checkpoint_path)
        
        return ctx.results
```

### 🏗️ Phase 3 Project: Multi-Step Workflow Engine

**What you'll build:** A workflow engine that executes complex, multi-step AI tasks with branching, validation, and human approval.

**Features:**
- Visual workflow definition (JSON/YAML)
- Parallel step execution
- Automatic retry on failure
- Human-in-the-loop approval step
- Checkpoint/resume capability
- Execution logs and cost report

---

## 🗺️ PHASE 4 — Multi-Agent Systems (Weeks 10–13)

> **Goal:** Build systems where multiple Claude agents collaborate

### Week 10 — Agent Communication Patterns

#### Concepts to Learn
- [ ] Orchestrator-worker pattern
- [ ] Peer-to-peer agent communication
- [ ] Message passing between agents
- [ ] Agent personas and specialization
- [ ] Shared memory between agents
- [ ] Avoiding infinite loops

#### Core Patterns

**Pattern: Orchestrator + Specialized Workers**
```
User Request
     ↓
┌─────────────────┐
│   ORCHESTRATOR  │  ← Plans, delegates, synthesizes
│  (Claude Boss)  │
└────────┬────────┘
         │ delegates
    ┌────┴────────────────────────┐
    ↓           ↓                ↓
┌──────┐   ┌────────┐   ┌──────────────┐
│Coder │   │ Writer │   │  Researcher  │
│Agent │   │ Agent  │   │    Agent     │
└──────┘   └────────┘   └──────────────┘
```

**Exercise 10.1 — Orchestrator-Worker system**
```python
class AgentWorker:
    """A specialized sub-agent"""
    
    def __init__(self, name: str, specialty: str, tools: list = None):
        self.name = name
        self.specialty = specialty
        self.tools = tools or []
        self.client = anthropic.Anthropic()
        self.system = f"""You are {name}, a specialized AI agent.
Your expertise: {specialty}
You receive specific tasks and return structured results."""
    
    def execute(self, task: str) -> dict:
        messages = [{"role": "user", "content": task}]
        
        while True:
            kwargs = {
                "model": "claude-haiku-4-5-20251001",
                "max_tokens": 1000,
                "system": self.system,
                "messages": messages
            }
            if self.tools:
                kwargs["tools"] = self.tools
            
            response = self.client.messages.create(**kwargs)
            
            if response.stop_reason == "end_turn":
                return {"agent": self.name, "result": response.content[0].text}
            
            # Handle tool calls
            tool_results = self._handle_tools(response.content)
            messages.append({"role": "assistant", "content": response.content})
            messages.append({"role": "user", "content": tool_results})
    
    def _handle_tools(self, content):
        results = []
        for block in content:
            if block.type == "tool_use":
                result = self._execute_tool(block.name, block.input)
                results.append({
                    "type": "tool_result",
                    "tool_use_id": block.id,
                    "content": json.dumps(result)
                })
        return results


class MultiAgentOrchestrator:
    """Boss agent that coordinates workers"""
    
    def __init__(self):
        self.client = anthropic.Anthropic()
        self.workers: dict[str, AgentWorker] = {}
        
    def register_worker(self, worker: AgentWorker):
        self.workers[worker.name] = worker
        return self
    
    def run(self, user_task: str) -> str:
        worker_descriptions = "\n".join(
            f"- {name}: {w.specialty}" 
            for name, w in self.workers.items()
        )
        
        # Step 1: Orchestrator creates plan
        plan_response = self.client.messages.create(
            model="claude-haiku-4-5-20251001",
            max_tokens=500,
            system=f"""You are an orchestrator. Available workers:
{worker_descriptions}

Create a JSON execution plan: 
{{"steps": [{{"worker": "name", "task": "specific task", "depends_on": []}}]}}""",
            messages=[{"role": "user", "content": user_task}]
        )
        
        plan = json.loads(plan_response.content[0].text)
        
        # Step 2: Execute plan (respecting dependencies)
        results = {}
        for step in plan["steps"]:
            # Wait for dependencies
            dep_context = ""
            if step.get("depends_on"):
                dep_context = "\n".join(
                    f"Result from {d}: {results.get(d, 'pending')}"
                    for d in step["depends_on"]
                )
            
            task_with_context = step["task"]
            if dep_context:
                task_with_context = f"Context from previous steps:\n{dep_context}\n\nYour task: {step['task']}"
            
            worker = self.workers.get(step["worker"])
            if worker:
                result = worker.execute(task_with_context)
                results[step["worker"]] = result["result"]
        
        # Step 3: Synthesize final answer
        synthesis_input = "\n\n".join(
            f"[{agent}]:\n{result}" 
            for agent, result in results.items()
        )
        
        final = self.client.messages.create(
            model="claude-haiku-4-5-20251001",
            max_tokens=800,
            system="Synthesize the agent results into a coherent final response for the user.",
            messages=[{
                "role": "user",
                "content": f"Original task: {user_task}\n\nAgent results:\n{synthesis_input}"
            }]
        )
        
        return final.content[0].text
```

---

### Week 11 — Agent Safety & Reliability

#### Concepts to Learn
- [ ] Minimal footprint principle
- [ ] Permission boundaries
- [ ] Rate limiting agents
- [ ] Detecting agent loops
- [ ] Graceful degradation
- [ ] Audit logging

**Safety Checklist for Agents:**
```python
class SafeAgent:
    def __init__(self, max_iterations=10, max_cost_usd=0.10):
        self.max_iterations = max_iterations
        self.max_cost = max_cost_usd
        self.iterations = 0
        self.total_cost = 0.0
        self.action_log = []
    
    def _check_safety(self):
        if self.iterations >= self.max_iterations:
            raise RuntimeError(f"Safety: Max iterations ({self.max_iterations}) reached")
        if self.total_cost >= self.max_cost:
            raise RuntimeError(f"Safety: Max cost (${self.max_cost}) reached")
    
    def _detect_loop(self, new_action: str) -> bool:
        """Detect if agent is repeating actions"""
        recent = self.action_log[-5:] if len(self.action_log) >= 5 else self.action_log
        return recent.count(new_action) >= 3  # Same action 3+ times = loop
    
    def step(self, action: str, execute_fn):
        self._check_safety()
        
        if self._detect_loop(action):
            raise RuntimeError(f"Safety: Loop detected for action: {action}")
        
        self.action_log.append(action)
        self.iterations += 1
        
        return execute_fn()
```

---

### Week 12–13 — Full Multi-Agent Application

#### Advanced Patterns to Implement
- [ ] Sub-agent spawning (agents creating agents)
- [ ] Shared knowledge base between agents
- [ ] Agent disagreement resolution
- [ ] Consensus mechanisms
- [ ] Async agent communication with queues

### 🏗️ Phase 4 Project: Agent Swarm Application

**What you'll build:** "AI Startup Analyzer" — A multi-agent system that researches a startup idea, validates it, builds a business plan, and produces an investor pitch.

**Agents:**
| Agent | Role |
|-------|------|
| `ResearchAgent` | Market research, competitor analysis |
| `FinancialAgent` | Revenue projections, unit economics |
| `TechAgent` | Technical feasibility, stack recommendations |
| `MarketingAgent` | Go-to-market, customer personas |
| `CriticAgent` | Devil's advocate, find weaknesses |
| `SynthesizerAgent` | Combine all into investor pitch deck |

**File structure:**
```
startup_analyzer/
├── main.py
├── orchestrator.py
├── agents/
│   ├── base_agent.py
│   ├── research_agent.py
│   ├── financial_agent.py
│   ├── tech_agent.py
│   ├── marketing_agent.py
│   ├── critic_agent.py
│   └── synthesizer_agent.py
├── memory/
│   ├── shared_kb.py      # Shared knowledge base
│   └── agent_memory.py
├── tools/
│   ├── search_tool.py
│   └── calculator_tool.py
└── output/
    └── pitch_deck_generator.py
```

---

## 🗺️ PHASE 5 — Production & Deployment (Weeks 14–16)

> **Goal:** Ship a real product people can use

### Week 14 — API Design & Backend

#### Concepts to Learn
- [ ] FastAPI + Claude integration
- [ ] WebSocket streaming responses
- [ ] Rate limiting and queuing
- [ ] Session management
- [ ] Error handling and retries
- [ ] Observability (logging, tracing)

**Exercise 14.1 — Production FastAPI server**
```python
from fastapi import FastAPI, HTTPException
from fastapi.responses import StreamingResponse
import anthropic
import asyncio

app = FastAPI()
client = anthropic.AsyncAnthropic()  # Use async client!

@app.post("/chat/stream")
async def stream_chat(request: dict):
    async def generate():
        async with client.messages.stream(
            model="claude-haiku-4-5-20251001",
            max_tokens=1000,
            messages=request.get("messages", [])
        ) as stream:
            async for text in stream.text_stream:
                yield f"data: {json.dumps({'text': text})}\n\n"
        yield "data: [DONE]\n\n"
    
    return StreamingResponse(generate(), media_type="text/event-stream")

@app.post("/agent/run")
async def run_agent(task: str, session_id: str):
    # Run agent asynchronously, return job ID
    job_id = f"job_{session_id}_{int(time.time())}"
    asyncio.create_task(run_agent_background(job_id, task))
    return {"job_id": job_id, "status": "started"}
```

---

### Week 15 — Frontend & UX

#### Build a full-stack AI app with:
- [ ] React/Next.js frontend
- [ ] Real-time streaming UI
- [ ] Agent progress visualization
- [ ] Cost tracking dashboard
- [ ] Conversation history

---

### Week 16 — Deployment & Monitoring

#### Production Checklist
- [ ] Environment variables for API keys
- [ ] Rate limiting per user
- [ ] Cost alerts (set budget limits)
- [ ] Error monitoring (Sentry)
- [ ] Response caching (Redis)
- [ ] A/B testing different prompts
- [ ] Usage analytics

### 🏗️ Phase 5 Project: Ship a Real Product

**Ideas (pick one):**
1. **AI Code Review Bot** — GitHub PR reviewer using multi-agent system
2. **Research Agent SaaS** — Upload docs, ask questions, get cited answers
3. **Content Pipeline** — Brief → Research → Write → Edit → SEO
4. **AI Meeting Assistant** — Transcribe → Summarize → Action items → Followup drafts

---

## 📚 Resources & References

### Official Docs
- 📖 [Anthropic API Docs](https://docs.anthropic.com)
- 🔧 [Anthropic SDK (Python)](https://github.com/anthropic-ai/anthropic-sdk-python)
- 📋 [Model Comparison](https://docs.anthropic.com/en/docs/about-claude/models)
- 🏗️ [Claude for Agents Guide](https://docs.anthropic.com/en/docs/build-with-claude/agentic-loop)

### Cost Calculators
- Use `client.messages.count_tokens()` before calls
- [Anthropic Pricing](https://anthropic.com/pricing)

### Recommended Project Stack
```
Python 3.11+
anthropic>=0.40.0
fastapi + uvicorn      # API backend
sqlite3                # Local memory (free)
python-dotenv          # Environment config
rich                   # Beautiful CLI output
pytest                 # Testing
```

### Setup
```bash
pip install anthropic fastapi uvicorn python-dotenv rich pytest

# .env file
ANTHROPIC_API_KEY=your_key_here
DEFAULT_MODEL=claude-haiku-4-5-20251001
MAX_COST_PER_RUN=0.05
```

---

## 🧪 Testing Without Burning Credits

```python
# Mock client for unit tests — $0 cost
class MockAnthropicClient:
    def __init__(self, fixed_response: str = "Mock response"):
        self.fixed_response = fixed_response
        self.call_count = 0
    
    def create(self, **kwargs):
        self.call_count += 1
        return MockResponse(self.fixed_response)

# In tests:
def test_my_agent():
    mock_client = MockAnthropicClient("Test output")
    agent = MyAgent(client=mock_client)
    result = agent.run("test input")
    assert result is not None
    assert mock_client.call_count == 1  # Verify exactly 1 API call made
```

---

## 📅 Weekly Schedule Suggestion

| Time | Activity |
|------|----------|
| Mon/Wed/Fri | Learn concepts + code exercises (2 hrs) |
| Sat | Work on project (3–4 hrs) |
| Sun | Review, refactor, document (1–2 hrs) |

**Total:** ~10–12 hrs/week → Complete in 14–16 weeks

---

## 🎯 Milestones & Checkpoints

| Week | Milestone | Deliverable |
|------|-----------|-------------|
| 3 | Phase 1 Complete | Research Assistant CLI working |
| 6 | Phase 2 Complete | Knowledge Base with RAG |
| 9 | Phase 3 Complete | Workflow Engine with branching |
| 13 | Phase 4 Complete | Multi-agent swarm application |
| 16 | Phase 5 Complete | Deployed production app |

---

## 💡 Key Principles to Always Remember

1. **Start with Haiku** — It's 12x cheaper than Sonnet. Only upgrade for final demos.
2. **Mock in tests** — Never burn real credits on unit tests.
3. **Cache aggressively** — Long system prompts cached = 90% token savings.
4. **One tool at a time** — Build tool by tool, test each before adding more.
5. **Human in the loop** — Production agents should have approval gates for irreversible actions.
6. **Minimal footprint** — Agents should request only the permissions they need.
7. **Log everything** — You can't debug what you can't see.
8. **Fail gracefully** — Every agent loop needs a max iteration + cost limit.

---

*Built for: Kerala → World 🌍 | Start date: ________ | Target: Multi-Agent AI Developer*