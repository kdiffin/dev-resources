
# AI Engineering Roadmap — 6 Weeks

## Vision and Purpose

The goal is not to become an ML researcher in 6 weeks.

The goal is to become an AI systems engineer: someone who can build, deploy, debug, evaluate, and operate real LLM-powered systems.

This roadmap assumes you already understand basic ML/DL, software engineering, APIs, infra, and distributed systems. So the focus is not “learn Python” or “train CNNs.” The focus is:

- transformers and LLM foundations
- inference and local model serving
- embeddings and RAG
- agents and orchestration
- evals and observability
- production deployment
- one serious end-to-end project

The core mindset shift:

> LLMs are not magic products. They are probabilistic components inside larger distributed systems.

A good AI engineer does not only prompt models.  
A good AI engineer builds the system around the model.

---

# Table of Contents

1. Core Direction
2. What to Ignore for Now
3. Main Resources
4. 5-Day Sprint
5. 6-Week Roadmap
6. Final Project Requirements
7. Expected Outcome
8. Concise Resource List

---

# 1. Core Direction

Modern AI engineering is mostly about:

- LLM application architecture
- retrieval systems
- context engineering
- agent workflows
- tool calling
- evals
- inference serving
- deployment
- observability
- reliability
- cost/latency tradeoffs

It is closer to backend/platform/distributed systems engineering than pure ML research.

The important progression is:

```text
Transformers
→ LLM internals
→ Inference
→ Embeddings
→ RAG
→ Agents
→ Evals
→ Production systems
→ Real deployed project
````

Your advantage is systems thinking.

If you already understand APIs, Kafka, Kubernetes, observability, deployment, and async workflows, then AI engineering maps naturally onto what you already know.

---

# 2. What to Ignore for Now

Low-priority for this 6-week sprint:

* spending weeks on classical ML
* CNN/RNN deep dives
* Kaggle-style projects
* deriving every transformer gradient
* training large models from scratch
* reading Deep Learning cover-to-cover
* random LangChain tutorials without understanding architecture
* building 10 toy chatbots

High-priority:

* understand transformers enough
* build RAG properly
* build agent workflows properly
* understand inference tradeoffs
* add evals and tracing
* deploy one serious system

---

# 3. Main Resources

## Core Books

### AI Engineering — Chip Huyen

Main production AI book.

Use this for:

* AI engineering mindset
* model selection
* RAG
* agents
* evals
* latency/cost tradeoffs
* production system design

This is probably the highest ROI book for the actual job of building AI systems.

### Build a Large Language Model From Scratch — Sebastian Raschka

Use this for:

* tokenization
* attention
* transformer blocks
* GPT architecture
* training/inference intuition

This is the best book for understanding how LLMs work internally without getting lost in research papers.

### Designing Machine Learning Systems — Chip Huyen

Use this for:

* production ML architecture
* data pipelines
* deployment
* monitoring
* ML system thinking

Still useful even though it is broader than GenAI.

### Hands-On Large Language Models

Use this for:

* practical LLM applications
* embeddings
* RAG
* model usage
* real examples

Good companion book.

---

## Core Courses / Free Resources

### Karpathy Zero-to-Hero

Use for:

* neural network intuition
* GPT from scratch
* tokenizer intuition
* transformer foundations

### Hugging Face LLM Course

Use for:

* practical model usage
* transformers library
* tokenizers
* inference
* fine-tuning basics

### Full Stack Deep Learning

Use for:

* production ML/AI systems
* deployment
* project structure
* AI product engineering

### Stanford CS25 Transformers

Use selectively for:

* transformer intuition
* modern LLM architecture
* advanced concepts

---

## Core Docs

Use docs like engineering manuals, not like books.

* Ollama docs
* vLLM docs
* Qdrant docs
* LangGraph docs
* MCP docs
* OpenAI evals docs
* LangChain/LlamaIndex RAG docs

---

# 4. 5-Day Sprint

Purpose:

Use the 5 free days to build momentum fast.
Do not just watch videos. Build every day.

By the end of 5 days, you should have a working mini AI system with:

* local model inference
* embeddings
* vector DB
* RAG
* basic tool-calling agent
* simple observability/eval logic

Not perfect. Working.

---

## Day 1 — Transformers Properly

### Learn

* The Illustrated Transformer
* Karpathy Intro to LLMs
* Karpathy Let’s Build GPT
* first chapters of Build a Large Language Model From Scratch

### Understand

* tokens
* embeddings
* self-attention
* multi-head attention
* positional encoding
* transformer blocks
* next-token prediction
* inference vs training
* KV cache

### Build

* tiny tokenizer experiment
* tiny attention mechanism in PyTorch
* simple next-token generation loop
* inspect how text becomes tokens

### Outcome

You should be able to explain:

```text
Text → tokens → embeddings → transformer blocks → logits → next token
```

And you should understand why attention is the core mechanism.

---

## Day 2 — Local LLM Stack

### Learn

* Ollama basics
* vLLM basics
* Hugging Face inference basics

### Do

Install and run local models:

* Qwen
* Llama
* Gemma
* Mistral or similar

### Experiment

Compare:

* small vs larger models
* quantized vs non-quantized models
* latency
* memory usage
* context window behavior
* streaming responses

### Build

* local OpenAI-compatible API wrapper
* simple chat endpoint
* streaming response endpoint

### Outcome

You should understand inference practically:

* why local serving is hard
* why quantization matters
* why latency matters
* why VRAM/RAM matters
* why API abstraction hides complex infra

---

## Day 3 — Embeddings and RAG

### Learn

* embeddings
* cosine similarity
* vector databases
* chunking
* retrieval
* reranking
* grounding
* citations

### Use

* Qdrant
* LangChain or LlamaIndex
* local embedding model or API embedding model

### Build

A RAG pipeline:

```text
Documents
→ chunking
→ embeddings
→ vector DB
→ retrieval
→ prompt assembly
→ LLM answer
→ citation output
```

### Add

* PDF/doc ingestion
* semantic search endpoint
* top-k retrieval
* citation source tracking
* simple reranking if possible

### Outcome

You should understand why RAG fails:

* bad chunks
* bad embeddings
* bad retrieval
* too much context
* missing reranking
* weak citations
* model hallucination

This is one of the most important days.

---

## Day 4 — Agents and Workflows

### Learn

* LangGraph
* MCP
* tool calling
* ReAct
* state machines
* human approval loops

### Core Realization

Agents are not magic.

They are usually:

```text
LLM + tools + state + workflow + retries + policy
```

A good agent system is basically a workflow engine with probabilistic reasoning inside it.

### Build

* tool-calling agent
* retrieval tool
* calculator/tool example
* file/document search tool
* human approval step
* retry/fallback logic
* simple state graph

### Outcome

You should understand:

* when agents are useful
* when agents are overkill
* why deterministic workflows often beat “free-form agents”
* why LangGraph-style orchestration matters
* why observability is mandatory

---

## Day 5 — Productionize the Mini-System

### Add

* Docker
* API layer
* streaming
* logging
* tracing
* basic evals
* retries
* error handling
* persistent vector DB
* simple dashboard or CLI

### Build Final 5-Day Output

A working mini AI engineering system:

```text
User query
→ API
→ retrieve context
→ agent decides action
→ optional tool call
→ LLM response
→ citations
→ logs/traces
→ simple eval result
```

### Outcome

By the end of 5 days, you should have a project that is clearly above tutorial level.

Not production-perfect.
But architecturally real.

---

# 5. 6-Week Roadmap

## Week 1 — Transformers and LLM Foundations

### Main Resources

* The Illustrated Transformer
* Attention Is All You Need
* Karpathy Zero-to-Hero
* Build a Large Language Model From Scratch

### Focus

* tokenization
* embeddings
* self-attention
* transformer blocks
* GPT architecture
* next-token prediction
* KV cache
* inference vs training

### Build

* tiny GPT/attention implementation
* tokenizer experiments
* minimal generation loop

### Output

You can explain how LLMs work internally without handwaving.

---

## Week 2 — Modern LLM Stack and Inference

### Main Resources

* Hugging Face LLM Course
* Ollama docs
* vLLM docs
* Build a Large Language Model From Scratch

### Focus

* model architectures
* quantization
* LoRA/QLoRA
* context windows
* serving models
* streaming
* batching
* GPU/VRAM tradeoffs
* OpenAI-compatible APIs

### Build

* local inference server
* streaming chat API
* quantized model benchmark
* model comparison notes

### Output

You understand what happens behind an LLM API.

---

## Week 3 — Embeddings, Retrieval, and RAG

### Main Resources

* AI Engineering — Chip Huyen
* Designing Machine Learning Systems
* Qdrant docs
* LangChain/LlamaIndex RAG docs

### Focus

* embeddings
* vector search
* chunking
* metadata
* hybrid search
* reranking
* grounding
* citations
* retrieval evaluation

### Build

* production-style RAG pipeline
* document ingestion
* vector DB
* retrieval API
* citations
* reranking
* hallucination tests

### Output

You can build and debug RAG systems beyond “chat with PDF.”

---

## Week 4 — Agents and Orchestration

### Main Resources

* LangGraph docs
* MCP docs
* ReAct paper
* AI Engineering — Chip Huyen

### Focus

* tool calling
* agent loops
* workflow graphs
* state machines
* planning
* memory
* approval loops
* retries
* fallbacks
* multi-agent limits

### Build

* agent with tools
* RAG tool
* approval workflow
* stateful graph
* async task execution
* optional Kafka integration

### Output

You understand agents as controlled workflows, not magic autonomous beings.

---

## Week 5 — Production AI Systems

### Main Resources

* AI Engineering — Chip Huyen
* Full Stack Deep Learning
* OpenAI evals docs
* W&B reports/blogs
* Chip Huyen blog

### Focus

* evals
* tracing
* observability
* prompt/version management
* routing
* caching
* latency
* cost
* safety
* regression testing
* model fallback

### Build

* eval dataset
* automated eval runner
* tracing/observability layer
* prompt versioning
* fallback routing
* basic metrics dashboard

### Output

You can reason about whether an AI system actually works.

---

## Week 6 — Serious Final Project

### Goal

Build one real deployed system.

Not a toy chatbot.

Pick one:

* Telco RCA agent
* Kubernetes diagnosis agent
* Security investigation assistant
* AI NOC assistant
* Internal documentation copilot
* Kafka incident analysis agent
* Engineering support copilot

### Required Features

The final project must include:

* LLM inference
* RAG
* vector DB
* agent/tool workflow
* citations
* streaming response
* evals
* observability
* retries/fallbacks
* API layer
* Docker deployment
* optional Kubernetes deployment
* optional Kafka async pipeline
* human approval loop

### Ideal Architecture

```text
User / Event
→ API Gateway
→ Orchestrator / LangGraph
→ Retrieval Layer
→ Vector DB
→ Tool Calls
→ LLM Inference
→ Eval / Guardrail Layer
→ Response / Ticket / Dashboard
→ Logs / Traces / Metrics
```

### Output

A serious AI engineering portfolio project.

This matters more than certificates.

---

# 6. Final Project Requirements

The final project should prove that you can build AI systems, not just use AI libraries.

Minimum acceptable version:

```text
FastAPI backend
+ local or API LLM
+ Qdrant
+ RAG
+ LangGraph agent
+ citations
+ tracing/logging
+ eval script
+ Docker Compose
```

Strong version:

```text
FastAPI backend
+ local inference with Ollama/vLLM
+ Qdrant
+ hybrid RAG
+ reranking
+ LangGraph
+ MCP-style tools
+ Kafka async event input
+ PostgreSQL for results
+ dashboard
+ eval pipeline
+ observability
+ Kubernetes deployment
```

Best version for your background:

```text
Telco/K8s RCA AI System

Alarm or incident comes in
→ Kafka topic
→ agent workflow starts
→ retrieves docs/runbooks
→ checks tools/APIs
→ produces RCA hypothesis
→ cites evidence
→ creates human-reviewable ticket
→ logs traces/evals
→ dashboard shows result
```

This aligns perfectly with systems/infra/telco AI engineering.

---

# 7. Expected Outcome

## After 5 Days

You should be able to:

* explain transformers at a practical level
* run local LLMs
* serve a model behind an API
* build a basic RAG system
* use a vector DB
* create a basic tool-calling agent
* add logs/traces
* build a working mini AI system

You will not be an expert yet.

But you should no longer be at “prompt engineering tutorial” level.

Expected level:

```text
Junior-to-mid practical AI systems builder
```

---

## After 6 Weeks

You should be able to:

* architect production RAG systems
* debug retrieval quality
* design agent workflows
* reason about inference bottlenecks
* create eval pipelines
* add observability
* deploy AI services
* understand local/on-prem AI constraints
* build AI systems around real operational workflows

Expected level:

```text
Strong AI engineering foundation
Infra-oriented LLM engineer
Production AI systems engineer trajectory
```

You will not be:

* LLM researcher
* frontier model trainer
* transformer architecture scientist

But you can realistically become strong at:

* enterprise AI systems
* on-prem AI
* AI platform engineering
* RAG/agent systems
* AI workflow automation
* infra-heavy GenAI applications

---

# 8. Concise Resource List

## Books

### Must Read

AI Engineering — Chip Huyen
Production GenAI systems, evals, RAG, agents, model selection, latency/cost tradeoffs.

Build a Large Language Model From Scratch — Sebastian Raschka
Best practical path to understanding transformer/LLM internals.

Designing Machine Learning Systems — Chip Huyen
Production ML architecture, deployment, monitoring, data/system thinking.

Hands-On Large Language Models
Practical LLM applications, RAG, embeddings, and implementation patterns.

### Optional Reference

Deep Learning — Goodfellow/Bengio/Courville
Reference only. Do not read cover-to-cover during this sprint.

NLP with Transformers
Good Hugging Face practical companion.

---

## Courses

Karpathy Zero-to-Hero
Best intuition for neural nets and GPT internals.

Hugging Face LLM Course
Best practical free LLM course.

Full Stack Deep Learning
Best production AI/ML engineering course.

Stanford CS25 Transformers
Good advanced transformer lectures.

---

## Docs

Ollama
Local model running.

vLLM
Production inference serving.

Qdrant
Vector database and semantic search.

LangGraph
Agent/workflow orchestration.

MCP
Tool integration standard.

OpenAI Evals
Evaluation concepts and patterns.

LangChain / LlamaIndex RAG docs
Useful implementation references.

---

# Final Rule

Do not optimize for finishing resources.

Optimize for building understanding and shipping one real system.

The correct loop is:

```text
Learn concept
→ implement small version
→ break it
→ debug it
→ write notes
→ integrate into final project
```

By the end, the project is the proof.

```
```
