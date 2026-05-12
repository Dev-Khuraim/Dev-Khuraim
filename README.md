<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=28&pause=1000&color=6366F1&center=true&vCenter=true&width=700&lines=Senior+AI+%26+Data+Engineer;LLM+Agents+%7C+RAG+Systems+%7C+Voice+AI;Building+AI+that+solves+real+problems" alt="Typing SVG" />

<br/>

[![Upwork](https://img.shields.io/badge/Available_on_Upwork-14a800?style=for-the-badge&logo=upwork&logoColor=white)](https://www.upwork.com/freelancers/YOUR_PROFILE)
[![Email](https://img.shields.io/badge/shaikhkhuraim3%40gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:shaikhkhuraim3@gmail.com)
[![Open to Work](https://img.shields.io/badge/Open_to_Freelance-6366F1?style=for-the-badge)](mailto:shaikhkhuraim3@gmail.com)

</div>

---

I'm a **Senior AI/Data Engineer** with 4+ years building production-grade LLM systems, agentic pipelines, and data infrastructure. I don't build demos — I build systems that run in production: async job queues, webhook-driven architectures, real-time WebSocket pipelines, and multi-provider AI abstractions with proper error handling and observability.

**What I specialise in:**
- 🤖 LLM agents & multi-step reasoning (LangGraph, LangChain, tool-calling)
- 🔍 RAG systems — hybrid search, reranking, evaluation
- 🗣️ Voice AI — real-time STT/TTS pipelines
- 🧪 LLM evaluation — metrics, regression detection, A/B testing
- 🗄️ Data engineering — ETL, schema introspection, NL→SQL
- ⚙️ Production APIs — FastAPI, async queues (Redis/RQ), PostgreSQL, Docker

---

## 🚀 Featured Projects

### 1 · [github-pr-intelligence](https://github.com/YOUR_USERNAME/github-pr-intelligence)
> **AI-powered GitHub App that reviews every pull request automatically**

A real GitHub App (not a toy) using HMAC-SHA256 webhook verification, GitHub App JWT authentication, and a two-pass LLM review engine. Posts **inline comments on exact diff lines** via the GitHub Review API, assigns risk labels (low/medium/high/critical), and processes jobs asynchronously via Redis + RQ so webhooks always return 200 immediately.

```
Webhook → HMAC verify → Redis/RQ → GitHub PR files
→ Pass 1: per-file analysis (security, logic, OWASP)
→ Pass 2: overall PR summary + risk score 0-100
→ Inline comments on diff lines + labels → PostgreSQL history
```

**Stack:** `FastAPI` `Redis + RQ` `PostgreSQL` `LangChain` `Claude/GPT-4o` `pyjwt` `Streamlit`

---

### 2 · [hybrid-rag-api](https://github.com/YOUR_USERNAME/hybrid-rag-api)
> **Production RAG with dense + sparse search, Cohere reranking, and RAGAS evaluation**

Goes beyond basic vector search — combines **pgvector cosine similarity** and **BM25Okapi** via **Reciprocal Rank Fusion (RRF)**, then passes candidates through a **Cohere cross-encoder reranker** for precision. Includes a full RAGAS evaluation pipeline (faithfulness, answer relevancy, context precision, context recall) so you can actually measure retrieval quality.

```
PDF/TXT upload → pdfplumber → chunking → OpenAI embeddings → pgvector
                                                        + BM25 index
Query → dense (top-20) + sparse (top-20) → RRF fusion
      → Cohere rerank (top-5) → GPT-4o generation → RAGAS eval
```

**Stack:** `FastAPI` `PostgreSQL + pgvector` `rank-bm25` `Cohere` `LangChain` `RAGAS` `Streamlit`

---

### 3 · [nl2sql-analyst](https://github.com/YOUR_USERNAME/nl2sql-analyst)
> **Schema-aware NL→SQL with self-healing retry and Plotly auto-visualisation**

Introspects live database schemas (tables, columns, types, sample values, row counts) and injects them into dialect-aware prompts. When generated SQL fails execution, a **self-correction loop** feeds the error + failed SQL back to the LLM for up to 3 retries. Supports SQLite, PostgreSQL, and MySQL. Auto-suggests the right chart type (bar, line, pie, scatter, metric) based on result shape.

```
NL question → schema introspection → LLM SQL generation
→ SQL safety check (blocks non-SELECT)
→ execute → on error: LLM correction loop (×3)
→ auto-chart suggestion → Plotly render
```

**Stack:** `FastAPI` `SQLAlchemy` `SQLite/PostgreSQL/MySQL` `LangChain` `Plotly` `Streamlit`

---

### 4 · [voice-ai-agent](https://github.com/YOUR_USERNAME/voice-ai-agent)
> **Real-time voice assistant: WebSocket audio → Whisper → LangGraph agent → TTS**

Full real-time voice pipeline over a single WebSocket connection. The browser records audio via `MediaRecorder`, sends base64-encoded webm to FastAPI, which transcribes it with **OpenAI Whisper**, runs a **LangGraph ReAct agent** with live tools (calculator, weather, web search, datetime), synthesises the response with **OpenAI TTS**, and streams MP3 audio back — all in one round trip. Supports local Whisper via faster-whisper for zero-cost offline transcription.

```
Browser MediaRecorder → WebSocket → Whisper STT → transcript
→ LangGraph ReAct agent (tools: calculate, weather, search, datetime)
→ OpenAI TTS → base64 MP3 → WebSocket → Web Audio API playback
```

**Stack:** `FastAPI WebSockets` `OpenAI Whisper` `LangGraph` `OpenAI TTS` `faster-whisper` `Vanilla JS`

---

### 5 · [llm-eval-platform](https://github.com/YOUR_USERNAME/llm-eval-platform)
> **Prompt versioning, A/B testing, and regression detection for LLM apps**

A complete evaluation platform for LLM applications. Version your prompts (semver), build golden datasets, run evals with 4 metrics concurrently, compare runs A/B, and automatically detect regressions when a new prompt version scores worse than the baseline. Runs LLM calls in a `ThreadPoolExecutor` with bounded concurrency and commits results incrementally.

```
Prompt v1 (baseline) ──┐
                        ├── Eval Run → exact_match + rouge_l + semantic_sim + llm_judge
Prompt v2 (candidate) ──┘
                          → aggregate scores → regression check (>5% drop = flagged)
                          → A/B radar chart in dashboard
```

**Stack:** `FastAPI` `SQLite/PostgreSQL` `OpenAI` `Anthropic` `rouge-score` `Plotly` `Streamlit`

---

## 🛠️ Tech Stack

**AI / LLM**

![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat&logo=langchain&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat&logo=langchain&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat&logo=openai&logoColor=white)
![Anthropic](https://img.shields.io/badge/Anthropic_Claude-D97706?style=flat)
![Ollama](https://img.shields.io/badge/Ollama-000000?style=flat)
![Whisper](https://img.shields.io/badge/Whisper_STT-412991?style=flat&logo=openai&logoColor=white)
![Cohere](https://img.shields.io/badge/Cohere-D8B4FE?style=flat)

**Backend & APIs**

![Python](https://img.shields.io/badge/Python_3.11-3776AB?style=flat&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![WebSockets](https://img.shields.io/badge/WebSockets-010101?style=flat)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat&logo=redis&logoColor=white)
![RQ](https://img.shields.io/badge/RQ_Workers-DC382D?style=flat)

**Data & Storage**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?style=flat&logo=postgresql&logoColor=white)
![pgvector](https://img.shields.io/badge/pgvector-336791?style=flat&logo=postgresql&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-CC2927?style=flat)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat&logo=sqlite&logoColor=white)

**DevOps & Infra**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat&logo=githubactions&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat&logo=streamlit&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-3F4F75?style=flat&logo=plotly&logoColor=white)

---

## 💼 What I build for clients

| Need | What I deliver |
|------|---------------|
| **AI code review / DevOps automation** | GitHub Apps, CI/CD integrations, LLM-powered quality gates |
| **Document intelligence** | Extract structured data from PDFs, invoices, contracts at scale |
| **RAG / Knowledge base systems** | Hybrid search, reranking, hallucination-resistant Q&A over your documents |
| **Voice AI products** | Real-time STT → agent → TTS pipelines for customer support or internal tools |
| **NL→SQL / Data analytics** | Natural language interface on top of your existing databases |
| **LLM evaluation & observability** | Metrics, regression detection, prompt versioning for production LLM apps |
| **Workflow automation** | Webhook-driven multi-step AI pipelines replacing manual processes |

---

## 📊 GitHub Stats

<div align="center">

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=YOUR_USERNAME&show_icons=true&theme=tokyonight&hide_border=true&count_private=true)
&nbsp;
![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=YOUR_USERNAME&layout=compact&theme=tokyonight&hide_border=true)

</div>

---

## 🤝 Let's work together

I'm **actively available for freelance contracts** — short-term builds, long-term retainers, and everything in between.

Best way to reach me:

- 💼 **Upwork:** [upwork.com/freelancers/YOUR_PROFILE](https://www.upwork.com/freelancers/YOUR_PROFILE)
- 📧 **Email:** [shaikhkhuraim3@gmail.com](mailto:shaikhkhuraim3@gmail.com)

> Remote · Worldwide · Fast turnaround
