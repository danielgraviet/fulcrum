# Phase 1: Foundation + Architecture Slice

## Goal
Stand up a runnable vertical slice of the project with a clear backend/frontend boundary and deterministic local data.

## Learning objectives
- Understand how to scope a hackathon build around demo-critical flows.
- Practice separating simulation logic from presentation logic.
- Compare frontend and backend stack pairings for speed of implementation.

## Build scope
- Initialize project structure for frontend + backend.
- Add a minimal API contract for simulation input/output.
- Add local JSON datasets for personas and demographics.
- Build one end-to-end "hello simulation" flow with mocked outputs.

## Tool/framework options to explore
- Frontend:
  - Next.js (App Router) + Tailwind + shadcn/ui for fastest UI scaffolding.
  - Vite + React + Tailwind if you want simpler build/runtime mental model.
- Backend:
  - FastAPI (recommended for Python speed + typed schemas).
  - Flask + Pydantic if you want minimal framework surface area.
- API schema:
  - Pydantic models for request/response and validation.
  - JSON Schema file to keep frontend/backend contract explicit.

## Completion checklist
- [ ] Create directories for `frontend/` and `backend/` (or equivalent split).
- [ ] Define simulation input schema (`headline`, `cta`, `audience_filters`, `sample_size`).
- [ ] Define simulation output schema (agent reactions + aggregate metrics).
- [ ] Create seed data files (`demographics.json`, `interests.json`, `locations.json`, `occupations.json`).
- [ ] Implement one API endpoint (`POST /simulate`) returning deterministic mock data.
- [ ] Implement one frontend page that can call `/simulate` and render raw JSON results.
- [ ] Add `README` run instructions that work from a clean clone.

## Deliverables
- Runnable frontend and backend locally.
- API schema definitions checked into source.
- Seed dataset JSON files with sample records.
- Basic integration from UI form -> API -> rendered response.

## Test path and passing criteria
- [ ] Backend unit test: schema validation accepts valid payload and rejects invalid payload.
- [ ] Backend API test: `POST /simulate` returns 200 + expected response keys.
- [ ] Frontend smoke test: page loads and submits form successfully.
- [ ] Manual path: run app, submit one ad payload, confirm response rendered in UI.
- Passing criteria:
  - All automated tests green.
  - No uncaught exceptions in local run logs.
  - Fresh environment startup documented and reproducible.

## Demo artifacts
- 20-30 second screen capture showing:
  - local app startup,
  - submitting a sample ad,
  - receiving simulation JSON response.
- One architecture diagram (simple boxes/arrows) matching actual repo layout.
