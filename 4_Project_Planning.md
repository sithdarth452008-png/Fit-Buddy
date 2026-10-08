# Project Planning

## FitBuddy — Development Phases, Milestones, Deliverables, and Verification Plan

## Implementation Phases

### Phase 1 — Foundation

Create the FastAPI application, dependency configuration, project structure, database connection, and base models.

### Phase 2 — Requirements & Validation

Implement Pydantic schemas, accepted goal/intensity/experience values, field limits, and form validation behavior.

### Phase 3 — Core Generation

Connect the workout and nutrition generation wrappers, store generated results, and render the result page.

### Phase 4 — Feedback Loop

Retrieve the latest plan, submit user feedback to the update service, persist the revised plan, and show the updated result.

### Phase 5 — Administration & APIs

Implement user listing, deletion, health monitoring, and JSON endpoints.

### Phase 6 — Testing & Documentation

Run endpoint tests, verify fallback behavior, document setup, and prepare demonstration material.

## Milestone Checklist

- **M1:** Project boots and home page renders.
- **M2:** User profile validates and persists.
- **M3:** Workout and nutrition outputs are generated and saved.
- **M4:** Feedback updates the latest plan.
- **M5:** Admin dashboard and delete operation work.
- **M6:** API tests pass and README setup instructions are complete.
- **M7:** Final demonstration can run with or without a configured Gemini key.

## Risk and Mitigation

- **AI service unavailable:** Use the implemented local fallback for development/testing.
- **Invalid user input:** Enforce Pydantic constraints and display form errors.
- **Database state affects repeated tests:** Use predictable test identifiers and reset/isolated test database strategy for larger deployments.
- **Model behavior changes:** Keep model names configurable through environment settings.
- **Wellness misuse:** Present the product as wellness guidance, not medical diagnosis or treatment.

## Suggested Project Schedule

For an academic project, the phases can be mapped to eight working sessions: ideation, requirements, design, planning, development, testing, documentation, and final demonstration.

Each session should end with a concrete artifact that can be reviewed before moving forward.

## Quick Reference

| Milestone | Primary Deliverable | Verification |
|---|---|---|
| M1 | Running skeleton | `GET /` returns 200 |
| M2 | Validated profile | Invalid values rejected |
| M3 | Generated plan | Workout + tip stored |
| M4 | Feedback revision | Updated plan returned |
| M5 | Admin/API layer | Users visible and deletable |
| M6 | Test suite | pytest passes |
| M7 | Demo package | README + presentation flow |

---

**Project basis:** This document is derived from the supplied FitBuddy source package, including its README, FastAPI routes, SQLAlchemy models, Jinja2 templates, CSS, and tests.
