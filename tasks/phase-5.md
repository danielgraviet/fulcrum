# Phase 5: Demo Hardening + Hackathon Polish

## Goal
Make the product demo-ready under hackathon constraints with stable behavior, a tight narrative, and fallback-safe execution.

## Learning objectives
- Practice reliability engineering for demo environments.
- Convert technical output into concise narrative insights.
- Build a repeatable demo flow that survives unpredictable conditions.

## Build scope
- Add insights summarizer and narrative output.
- Harden runtime behavior (latency, retries, offline fallback, deterministic seeds).
- Package a 90-second demo path with scripts and backup plans.

## Tool/framework options to explore
- Insight generation:
  - One-shot LLM summary from aggregated reactions.
  - Rule/template-based summarizer for guaranteed offline mode.
- Reliability and observability:
  - Structured logs (`loguru` or stdlib logging + JSON formatter).
  - Lightweight telemetry timing for generation/simulation/render stages.
- Presentation and deployment:
  - Local Docker Compose for one-command startup.
  - Vercel (frontend) + Render/Fly (backend) if you choose hosted demo.

## Completion checklist
- [ ] Implement insight summary output (top positives, complaints, recommendations).
- [ ] Add deterministic demo seed profile (e.g., `demo_genz_runner`).
- [ ] Add health checks and startup validation for required configs.
- [ ] Add graceful fallback if LLM provider is unavailable.
- [ ] Add script/Make target for one-command local launch.
- [ ] Write 90-second demo script aligned to actual UI flow.
- [ ] Create backup demo assets (screenshots/video) in case live run fails.

## Deliverables
- Stable demo build with deterministic scenario.
- Insight summary module and displayed narrative results.
- Runbook with startup commands and contingency steps.
- Final demo script and artifact package.

## Test path and passing criteria
- [ ] Integration test: end-to-end flow completes under demo config.
- [ ] Resilience test: simulate LLM failure and confirm fallback path works.
- [ ] Regression test: deterministic seed reproduces same top-line metrics.
- [ ] Manual rehearsal: run full 90-second demo flow at least 3 times.
- Passing criteria:
  - All critical-path tests pass.
  - Demo flow completes without manual patching.
  - Backup artifacts available and current.

## Demo artifacts
- Final 90-second demo video.
- One-page summary: problem, simulation method, key metrics, insights.
- Appendix assets: fallback screenshots, architecture diagram, test proof snapshots.
