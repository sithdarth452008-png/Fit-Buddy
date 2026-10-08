# Project Development

## FitBuddy — Implemented Modules, Workflows, APIs, and Development Details

## Implemented Backend

- **FastAPI application** initialized in `app/main.py`.
- **Database tables** created through SQLAlchemy metadata.
- **Routes** implemented for browser forms, admin view, deletion, JSON APIs, and health checks.
- **CRUD layer** handles profile upserts, plan creation, retrieval, updates, listing, and deletion.
- **Pydantic schemas** enforce valid ranges and enumerated values.

## AI Integration

The code separates AI responsibilities into a workout-plan generator, nutrition-tip generator, and feedback-driven update function.

The README specifies Gemini Pro for workout generation/update and Gemini Flash for nutrition tips, while model names remain configurable in the service layer.

If `GOOGLE_API_KEY` is not configured, the project provides deterministic fallback behavior for local testing.

## Main Workflow

### `POST /generate-workout`

```text
POST /generate-workout
    ↓
validate UserInput
    ↓
save_user()
    ↓
generate_workout_gemini()
    ↓
generate_nutrition_tip_with_flash()
    ↓
save_plan()
    ↓
render result.html
```

### `POST /submit-feedback`

```text
POST /submit-feedback
    ↓
validate FeedbackRequest
    ↓
get_user() + get_latest_plan()
    ↓
update_workout_plan()
    ↓
update_plan()
    ↓
render updated result.html
```

## API Surface

- **POST `/api/generate-workout`** — Creates/stores a user plan and returns workout + nutrition data.
- **POST `/api/submit-feedback`** — Revises the latest plan using feedback.
- **GET `/api/users`** — Returns stored user profiles.
- **GET `/health`** — Returns application status and Gemini configuration state.
- **GET `/docs`** — FastAPI-generated interactive API documentation.

## Frontend Implementation

The interface uses three Jinja2 templates:

- `index.html` collects the profile.
- `result.html` presents generated content and feedback controls.
- `all_users.html` provides the admin/coach view.

The CSS defines a responsive dark interface with cards, form controls, result sections, and mobile breakpoints.

---

**Project basis:** This document is derived from the supplied FitBuddy source package, including its README, FastAPI routes, SQLAlchemy models, Jinja2 templates, CSS, and tests.
