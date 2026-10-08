# Project Demonstration

## FitBuddy — End-to-End Demo Script and Presentation Checklist

## Demonstration Objective

Show the complete path from user profile entry to AI-generated plan, persistence, feedback-driven revision, and administrative review. The demonstration can be run with the Gemini service configured or with the deterministic local fallback.

## Demo Step 1 — Launch

```bash
uvicorn app.main:app --reload
```

Open the FitBuddy home page and briefly identify the landing page, AI fitness planner message, and profile form.

## Demo Step 2 — Create a Profile

Use a sample profile such as:

- **User ID:** FB001
- **Name:** Alex
- **Age:** 21
- **Weight:** 65 kg
- **Goal:** muscle gain
- **Intensity:** medium
- **Experience:** beginner

Submit the form.

Point out that the route validates the input, saves the user, generates the workout and nutrition outputs, stores the plan, and renders the result page.

## Demo Step 3 — Explain the Result

- **Profile summary:** Shows the values used for personalization.
- **Workout section:** Displays the seven-day plan.
- **Nutrition & Recovery section:** Displays the generated tip.
- **Feedback section:** Demonstrates the iterative AI workflow.

## Demo Step 4 — Feedback Loop

Enter feedback such as:

> Add more rest and mobility work.

Submit it and show the updated plan.

Explain that the application retrieves the latest plan, sends the original plan plus feedback to the update layer, stores the revised plan, and marks the result as updated.

## Demo Step 5 — Admin/Coach View

Open `/view-all-users`.

Show the stored user, profile values, original plan, and updated plan when available. Demonstrate the delete action only if appropriate for the presentation database.

## Demo Step 6 — API & Health

- Open `/docs` to show FastAPI's interactive API documentation.
- Call `/health` and show `status='ok'`.
- Optionally call `/api/users` to show persisted profiles.
- Explain that JSON endpoints make the backend usable by other clients.

## Closing Points

- FitBuddy combines AI generation with conventional web engineering rather than relying on AI alone.
- Validation and persistence make the workflow reproducible.
- The feedback loop turns a one-shot recommendation into an iterative user experience.
- Fallback behavior supports demonstrations without a live API key.
- The system is intended for wellness guidance and should not be presented as medical diagnosis or treatment.

---

**Project basis:** This document is derived from the supplied FitBuddy source package, including its README, FastAPI routes, SQLAlchemy models, Jinja2 templates, CSS, and tests.
