# Phase 2: Persona Generation Engine

## Goal
Generate believable synthetic audience members from local datasets using stratified sampling and reproducible randomness.

## Learning objectives
- Learn practical stratified sampling for synthetic test populations.
- Design persona schemas that are useful for downstream simulation.
- Build deterministic generation for repeatable demos and testing.

## Build scope
- Implement persona templates and segment weighting rules.
- Generate audience cohorts from filter inputs (age, location, income, interests).
- Persist generated personas for inspection and replay.

## Tool/framework options to explore
- Sampling logic:
  - Pure Python with `random.Random(seed)` for deterministic outputs.
  - `numpy` for weighted vectorized sampling if speed becomes relevant.
- Data validation:
  - Pydantic models for persona shape and constraints.
  - `pandera` if you want dataframe-style validation for larger synthetic datasets.
- Persistence:
  - JSONL files for easy debugging and replay.
  - SQLite (optional) if you want queryable cohorts without external infra.

## Completion checklist
- [ ] Create persona model with fields from README (id, age, gender, location, income, interests, personality, media_habits).
- [ ] Implement segment definitions and target distributions.
- [ ] Implement deterministic generator with configurable `seed`.
- [ ] Support configurable sample size (minimum 30, target 500).
- [ ] Add endpoint or service method to return generated personas.
- [ ] Add cohort export (`generated_personas.json` or JSONL).
- [ ] Add logging/metadata for generation run (`seed`, filters, sample size).

## Deliverables
- Persona generation module/service.
- Versioned seed/template data files.
- Example generated cohort file committed for reference.
- Short docs on distribution assumptions and limitations.

## Test path and passing criteria
- [ ] Unit test: same seed + same input -> identical persona output.
- [ ] Unit test: distribution checks remain within configured tolerance.
- [ ] Unit test: sample size exactly matches requested size.
- [ ] Contract test: generated persona objects always satisfy schema.
- [ ] Manual path: generate 500 personas and inspect 10 random records for realism.
- Passing criteria:
  - Determinism confirmed.
  - Distribution tests pass.
  - No schema violations in generated cohorts.

## Demo artifacts
- Table/grid screenshot of generated personas.
- Quick script output showing segment distribution summary (e.g., Gen Z %, income bands).
- 15-second walkthrough of "generate cohort with filters" action.
