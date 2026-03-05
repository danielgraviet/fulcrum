# Fulcrum

**Fulcrum is a synthetic audience simulator that predicts campaign performance before launch.**

It lets teams upload an ad concept, generate a realistic audience cohort, and watch 300-500 agents react in real time with predicted CTR, conversion, sentiment, and segment-level insights.

## Why This Is Useful
- Launch decisions move from opinion to simulation-backed evidence.
- Teams can test messaging with zero media spend.
- Results are explainable by audience segment, not just black-box scores.

## What Judges Can Expect In The Demo
1. Upload ad input (`image + headline + CTA`).
2. Pick audience filters (age, location, interests, income, sample size).
3. Run a live simulation where avatars react in waves.
4. See dashboard metrics and insight summary instantly.
5. Click any persona to inspect the "why" behind the reaction.

## Core Product Capabilities

### 1) Persona Generation
- Builds synthetic personas from local demographic and behavior templates.
- Uses stratified sampling to reflect target audience mix.
- Produces reproducible cohorts using a deterministic seed.

Example persona:
```json
{
  "id": 104,
  "age": 24,
  "gender": "female",
  "location": "Austin",
  "income": 52000,
  "interests": ["fitness", "instagram"],
  "personality": "impulse buyer",
  "media_habits": ["TikTok", "Instagram"]
}
```

### 2) Reaction Simulation
- Each persona evaluates the ad and returns:
  - scroll-stop score
  - click intent
  - purchase intent
  - one-line reaction text
- Supports two modes:
  - `instant`: fully local, rule-based probabilistic simulation
  - `hybrid`: small set of real LLM responses expanded to a large cohort

### 3) Live Reaction Wall
- Grid of audience avatars starts neutral, then reacts in animated waves.
- Behavior icons make outcomes immediately understandable:
  - `👍` click
  - `🛒` purchase
  - `❌` ignore
  - `😍` strong positive
  - `😐` neutral
  - `😡` negative

### 4) Insights + Analytics Dashboard
- Top-line metrics:
  - predicted CTR
  - predicted conversion
  - sentiment score
- Segment cuts:
  - CTR by demographic
  - sentiment by audience cluster
  - purchase probability curves
- Narrative insights:
  - top positives
  - top complaints
  - suggested messaging improvements

## System Design (Hackathon-Optimized)

```text
Frontend (Next.js + Tailwind + Framer Motion)
        |
        v
Simulation API (FastAPI)
        |
        +--> Persona Generator (local JSON templates)
        +--> Agent Simulator (instant/hybrid)
        +--> Aggregator (metrics + segment analysis)
        +--> Insight Generator (LLM or template fallback)
```

### Design Principles
- Built for a 24-48 hour hackathon window.
- Fast local-first execution with minimal infrastructure.
- No required production database for MVP.
- Demo-safe fallback behavior if external LLM services fail.

## Example Output
```text
Predicted CTR: 3.2%
Predicted Conversion: 0.8%
Sentiment: 64% positive
Top Complaint: Price clarity
Top Responding Segment: Gen Z runners
```

## 90-Second Demo Script
1. Upload a sports shoe ad.
2. Choose audience: US, ages 18-35, fitness + tech interests.
3. Run simulation for 500 agents.
4. Show reaction wall animate to completion.
5. Highlight metrics and top insight.
6. Open one persona card to show explainability.

## Tech Stack
- Python package/runtime: `uv`
- Backend: `FastAPI`
- LLM provider support: `OpenAI` (hybrid mode), with mock/template fallback
- Frontend target: `Next.js + Tailwind + Framer Motion + Recharts`
- Data: local JSON templates (no external DB required for MVP)

## Current Repo Status
This repository is currently in implementation phase.

Planned execution phases are documented in:
- [`tasks/phase-1.md`](tasks/phase-1.md)
- [`tasks/phase-2.md`](tasks/phase-2.md)
- [`tasks/phase-3.md`](tasks/phase-3.md)
- [`tasks/phase-4.md`](tasks/phase-4.md)
- [`tasks/phase-5.md`](tasks/phase-5.md)

## Local Quickstart
```bash
uv sync
uv run main.py
```

> Note: Full simulation API/UI endpoints are being built according to the phased plan in `tasks/`.

## Positioning
Fulcrum can be described as:

**"Monte Carlo-style market response simulation for creative and campaign decisions."**

That framing communicates scale, rigor, and business relevance immediately.
