# Brainstorming and Ideation

## FitBuddy — AI Fitness Plan Generator

### Project Concept & Idea Development

## Problem Identification

Many fitness applications provide generic routines or require users to manually assemble a plan. The FitBuddy concept addresses this by collecting a small fitness profile and producing a personalized seven-day workout plan together with a nutrition/recovery tip.

A second problem is that a generated plan may not remain suitable after the user tries it. FitBuddy therefore includes a feedback loop that accepts natural-language change requests and generates a revised plan.

## Core Idea

Build a lightweight web application that combines a FastAPI backend, Jinja2 user interface, SQLite persistence, and Google Gemini services. The system should remain testable even when an API key is absent, so a deterministic local fallback is provided.

- **Personalized inputs:** user ID, name, age, weight, goal, intensity, and experience level.
- **AI output:** a seven-day workout plan and a nutrition/recovery tip.
- **Iteration:** user feedback can trigger a revised workout plan.
- **Persistence:** users and plans are stored with SQLAlchemy.
- **Administration:** a dashboard lists stored users and plans and supports deletion.
- **Integration:** JSON endpoints support testing and future client integration.

## Proposed User Journey

**Profile → Generate → Review → Give Feedback → Regenerate**

The front page captures the profile. The backend validates and stores it, calls the AI generation layer, saves the resulting plan, and renders the result page. The user can then submit feedback to update the plan.

## Design Principles

- Simple onboarding with a small number of required fields.
- Separation of concerns between routes, persistence, validation, and AI service wrappers.
- Wellness guidance rather than medical diagnosis or treatment.
- Configurable AI model names and a safe local fallback for development.
- Testable HTTP endpoints in addition to browser-oriented routes.

---

**Project basis:** This document is derived from the supplied FitBuddy source package, including its README, FastAPI routes, SQLAlchemy models, Jinja2 templates, CSS, and tests.
