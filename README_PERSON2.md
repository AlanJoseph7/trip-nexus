# ⚙️ Person 2 — Specialist Agents, Grounding Tools, API Backend & Test Suite

Welcome to **Person 2**'s project package for **TripNexus**! You are the **Backend, Grounding Tools & Quality Assurance Lead**. Your focus is the deterministic engine, verified static catalog data, Express API routing, strict schema contracts, and the automated test suite.

---

## 📁 Your Files & Directory Structure

Place these files in your local clone preserving this exact hierarchy:

```
TripNexus/
├── artifacts/
│   └── api-server/
│       ├── build.mjs
│       ├── package.json
│       ├── tsconfig.json
│       └── src/
│           ├── app.ts                  # Express application setup & middleware
│           ├── index.ts                # Server entry point (starts HTTP server on PORT)
│           ├── data/                   # Verified static knowledge fixtures
│           │   ├── agents.json         # Agent definitions, descriptions & system prompts
│           │   ├── destinations.json   # 11 Indian destinations metadata
│           │   ├── places.json         # Geo-coordinates, entry fees, visiting times
│           │   ├── scenarios.json      # Test traveler profiles & constraints
│           │   └── weather.json        # Seasonal climate patterns across months
│           ├── routes/                 # REST API endpoints
│           │   ├── documentation.ts    # Documentation & schema routes
│           │   ├── health.ts           # Server healthcheck endpoint
│           │   ├── index.ts            # Route aggregator
│           │   └── trips.ts            # POST /api/plan-trip & GET /api/runs/:runId
│           ├── middlewares/
│           │   └── .gitkeep
│           └── trips/
│               ├── data.ts             # Static data loading & retrieval utilities
│               ├── tools.ts            # Deterministic tools (Haversine distance, INR math)
│               ├── orchestrator.test.ts# Vitest tests for agent orchestration
│               ├── groq.test.ts        # Vitest tests for Groq LLM integration
│               ├── offline-planner.test.ts # Vitest tests for offline fallback
│               ├── run-store.test.ts   # Vitest tests for in-memory run store
│               └── tools.test.ts       # Vitest tests for tool arithmetic & distance
└── lib/
    ├── api-spec/                       # OpenAPI contract definitions
    ├── api-zod/                        # Zod runtime validation schemas
    └── db/                             # Optional database persistence configuration
```

---

## 🛠️ Step-by-Step Git Commands (Your Push Sequence)

Once Person 1 merges `main`, you clone the repository and push your branch:

```bash
# 1. Clone the updated repo
git clone https://github.com/<your-org-or-username>/tripnexus.git
cd tripnexus

# 2. Checkout your feature branch
git checkout -b feature/specialist-tools-backend

# 3. Copy your Person 2 files into the repo folder preserving the directory structure

# 4. Stage your files
git add artifacts/api-server/src/trips/tools.ts
git add artifacts/api-server/src/trips/data.ts
git add artifacts/api-server/src/data/
git add artifacts/api-server/src/app.ts
git add artifacts/api-server/src/index.ts
git add artifacts/api-server/src/routes/
git add artifacts/api-server/src/middlewares/
git add artifacts/api-server/build.mjs
git add lib/
git add artifacts/api-server/src/trips/*.test.ts

# 5. Run tests to verify everything passes
pnpm test

# 6. Commit and push
git commit -m "feat(backend): add specialist agent tools, express routes, zod schemas, and vitest suite"
git push -u origin feature/specialist-tools-backend
```

> **Next Step**: Go to GitHub, open a **Pull Request** (`feature/specialist-tools-backend` -> `main`). Have your teammates review and merge it.

---

## 🎓 Viva & Oral Exam Defense Points (What You Should Say)

When the evaluator asks: **"What was your contribution to TripNexus?"**
* **Your Answer**:
  1. *"I developed the **Deterministic Grounding Tools** in `tools.ts`. LLMs are notorious for mathematical inaccuracies with currency sums and geographic coordinates. I separated deterministic calculations (Haversine formula for route distances and exact INR arithmetic for group budgets) from LLM reasoning."*
  2. *"I built the **Local Verified Datasets** in `data/`, covering 11 major destinations with verified place coordinates, visit durations, entrance fees, and historical seasonal climate patterns."*
  3. *"I architected the **Express API Endpoints** (`routes/trips.ts`) exposing `POST /api/plan-trip` and `GET /api/runs/:runId`, with strict Zod runtime schema validation to ensure input parameters (destination, dates, travelers, budget) are validated before execution."*
  4. *"I authored the comprehensive **Automated Vitest Test Suite** (`*.test.ts`) covering tool calculation precision, offline fallback stability, run store persistence, and mock agent handoffs."*
