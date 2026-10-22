# 🧠 Person 1 — AI Core, Multi-Agent Orchestration & Groq LLM Engine

Welcome to **Person 1**'s project package for **TripNexus**! You are the **AI Architecture & Multi-Agent Lead**. Your focus is the core intelligence of the system: orchestrating five autonomous agents, managing dynamic replanning loops, connecting to Groq Cloud LLMs with rate-limiting defenses, and handling deterministic offline fallbacks.

---

## 📁 Your Files & Directory Structure

Place these files in your clone/local folder preserving this exact hierarchy:

```
TripNexus/
├── .env.example
├── .gitignore
├── .npmrc
├── LICENSE
├── README.md
├── package.json
├── pnpm-lock.yaml
├── pnpm-workspace.yaml
├── tsconfig.base.json
├── tsconfig.json
└── artifacts/
    └── api-server/
        ├── package.json
        ├── tsconfig.json
        └── src/
            └── trips/
                ├── base-agent.ts       # Abstract agent class with tool access validation
                ├── groq.ts             # Groq LLM client, model failover, exponential backoff
                ├── model-provider.ts   # Model provider interface abstraction
                ├── offline-planner.ts  # Deterministic offline planner (runs if quota fails)
                ├── orchestrator.ts     # The central multi-agent orchestrator & state machine
                ├── run-store.ts        # In-memory execution trace storage
                ├── trace.ts            # Run trace event builder & typing
                └── types.ts            # Agent decisions, issues, & shared state interfaces
```

---

## 🛠️ Step-by-Step Git Commands (Your Push Sequence)

As Person 1, you initiate the repository and push the **AI Core & Orchestration Engine** branch:

```bash
# 1. Initialize Git in your project directory
git init
git remote add origin https://github.com/<your-org-or-username>/tripnexus.git

# 2. Create your feature branch
git checkout -b feature/agent-core-orchestrator

# 3. Stage your base configs and AI Core files
git add .

# 4. Verify that .env is NOT staged (only .env.example should be staged)
git status

# 5. Commit your work
git commit -m "feat(ai-core): implement multi-agent orchestrator, groq integration, and offline fallback"

# 6. Push your branch to GitHub
git push -u origin feature/agent-core-orchestrator
```

> **Next Step**: Go to GitHub, open a **Pull Request** (`feature/agent-core-orchestrator` -> `main`), and merge it into `main`.

---

## 🎓 Viva & Oral Exam Defense Points (What You Should Say)

When the evaluator asks: **"What was your contribution to TripNexus?"**
* **Your Answer**:
  1. *"I designed and built the **Multi-Agent Orchestrator** in `orchestrator.ts`. Instead of sending a single prompt to a monolithic LLM, TripNexus coordinates five autonomous agents: Trip Manager, Destination, Budget, Weather, and Critic."*
  2. *"I implemented the **Independent Critic Evaluation Loop**. The Critic agent audits the draft against date continuity, budget constraints, and weather risks. If it detects flaws, it returns a `REJECTED` decision with actionable issues, triggering a targeted revision to the responsible agent (bounded at 3 cycles to avoid infinite loops)."*
  3. *"I built the **Groq Cloud LLM engine** with rate-limit resilience. Free-tier accounts have tight limits, so I implemented automatic concurrency gating, header-respecting `Retry-After` backoff, and a model failover pool (`llama-3.3-70b-versatile` $\rightarrow$ `llama-3.1-8b-instant`)."*
  4. *"I authored the **Deterministic Offline Demo Planner** in `offline-planner.ts`. If an API key is missing or quota runs out, the system seamlessly produces a verified offline itinerary using local catalog data, ensuring zero application crashes."*
