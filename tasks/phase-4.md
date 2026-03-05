# Phase 4: Reaction Wall + Results Dashboard

## Goal
Build the visual demo centerpiece: animated synthetic audience wall plus actionable result dashboard.

## Learning objectives
- Turn backend simulation outputs into high-impact visual storytelling.
- Use animation intentionally to communicate system behavior.
- Design dashboards that prioritize judge-friendly signal over noise.

## Build scope
- Implement avatar grid/reaction wall with wave-based updates.
- Build key metric cards (CTR, conversion, sentiment).
- Add demographic breakdown charts and persona drill-down panel.

## Tool/framework options to explore
- UI animation:
  - Framer Motion for staggered reveal/wave animation.
  - CSS keyframes + requestAnimationFrame for lighter dependency footprint.
- Charts:
  - Recharts for fast React-native integration.
  - Tremor components for polished analytics visuals.
- State management:
  - React Query/TanStack Query for API state and retries.
  - Zustand for lightweight local simulation/session state.

## Completion checklist
- [ ] Create simulation page with ad preview + run button.
- [ ] Render 300-500 avatar cells with neutral initial state.
- [ ] Animate reaction updates over 2-3 seconds in randomized waves.
- [ ] Add legend for reaction icons and demographic color coding.
- [ ] Implement persona detail drawer/modal on avatar click.
- [ ] Implement results dashboard cards and at least two charts.
- [ ] Ensure responsive behavior for desktop and laptop demo sizes.

## Deliverables
- Working reaction wall component.
- Results dashboard view with aggregate and segmented metrics.
- Persona explorer interaction.
- Cohesive UI theme suitable for a live demo.

## Test path and passing criteria
- [ ] Frontend component tests: reaction wall renders target number of agents.
- [ ] Frontend behavior test: run simulation updates agent states and metrics.
- [ ] Frontend interaction test: clicking avatar opens correct persona details.
- [ ] Manual path: full run from upload/form input to animated results.
- Passing criteria:
  - No blocking UI errors during repeated simulation runs.
  - Animation completes reliably under typical laptop performance.
  - Key metrics and chart values match backend response data.

## Demo artifacts
- 30-45 second recording of full animated reaction wall run.
- Screenshot set: pre-run state, in-progress wave, completed metrics dashboard.
- Single slide with "what judges should notice" callouts.
