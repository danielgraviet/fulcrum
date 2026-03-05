# Phase 3: Reaction Simulation Core

## Goal
Implement agent reaction simulation with both instant heuristic mode and higher-fidelity LLM-seeded mode.

## Learning objectives
- Build a hybrid simulation architecture that balances realism and speed.
- Translate persona attributes into probabilistic behavioral outcomes.
- Design fallback modes so demos never fail due to external API issues.

## Build scope
- Implement scoring engine for `scroll_stop`, `click`, `purchase`, and sentiment.
- Generate one-line reaction text for each persona.
- Add two modes:
  - Instant mode: fully local probabilistic simulation.
  - Hybrid mode: 20-30 LLM responses expanded to larger synthetic cohort.

## Tool/framework options to explore
- Simulation logic:
  - Rule-based weighted scoring tables in YAML/JSON.
  - Logistic-style scoring using simple linear model coefficients.
- LLM integration:
  - OpenAI Python SDK for seeded response generation.
  - Anthropic SDK alternative if you want model/provider flexibility.
- Reliability:
  - Feature flag (`SIM_MODE=instant|hybrid`).
  - Cached LLM response store for consistent demo behavior.

## Completion checklist
- [ ] Define reaction schema (`stop_score`, `clicked`, `purchased`, `sentiment`, `reaction_text`).
- [ ] Implement deterministic instant-mode simulator.
- [ ] Implement hybrid-mode seed generation and cohort expansion.
- [ ] Add guardrails so hybrid mode gracefully falls back to instant mode.
- [ ] Expose mode selection through API and UI.
- [ ] Record per-run simulation metadata (mode, duration, seed, model used).

## Deliverables
- Simulation service module with both modes.
- Configurable rules file for score adjustments.
- Optional LLM adapter layer with provider abstraction.
- API output containing per-agent reactions and aggregate metrics.

## Test path and passing criteria
- [ ] Unit test: instant mode returns valid reaction for every persona.
- [ ] Unit test: edge cases (empty interests, missing optional fields) handled safely.
- [ ] Unit test: fallback activates when LLM call fails.
- [ ] Integration test: `/simulate` returns stable metrics for fixed seed.
- [ ] Manual path: run both modes and compare runtime + output realism.
- Passing criteria:
  - Instant mode runs reliably and fast locally.
  - Hybrid mode works when configured and degrades gracefully when unavailable.
  - Aggregate metrics internally consistent (e.g., purchases <= clicks <= agents).

## Demo artifacts
- Side-by-side capture of instant vs hybrid simulation outputs.
- Example agent reaction cards showing varied persona-specific responses.
- Runtime comparison snapshot (instant vs hybrid) for hackathon storytelling.
