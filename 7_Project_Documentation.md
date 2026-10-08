# Project Documentation

## FitBuddy — User Guide, Setup Guide, API Reference, and Operational Notes

## Project Overview

FitBuddy is a FastAPI + Jinja2 + SQLite application that generates personalized seven-day workout plans and nutrition/recovery tips, then allows users to refine the workout plan through feedback.

## Installation — Windows

```bat
py -m venv venv
venv\Scripts\activate
python -m pip install --upgrade pip
pip install -r requirements.txt
copy .env.example .env
```

Add the Gemini API key to `.env` when live AI generation is required.

## Running the Application

```bash
uvicorn app.main:app --reload
```

- **Home:** `http://127.0.0.1:8000`
- **Swagger/API docs:** `http://127.0.0.1:8000/docs`
- **Admin/coach dashboard:** `http://127.0.0.1:8000/view-all-users`
- **Health:** `http://127.0.0.1:8000/health`

## Using the Web Interface

1. Enter name and unique user ID.
2. Enter age and weight in kilograms.
3. Select fitness goal, workout intensity, and experience level.
4. Choose **Generate My Plan**.
5. Review the seven-day plan and nutrition/recovery tip.
6. Enter feedback when changes are required and submit the update.

## API Examples

### POST `/api/generate-workout`

```json
{
  "user_id": "FB001",
  "username": "Alex",
  "age": 21,
  "weight": 65,
  "goal": "muscle gain",
  "intensity": "medium",
  "experience": "beginner"
}
```

### POST `/api/submit-feedback`

```json
{
  "user_id": "FB001",
  "feedback": "Add more cardio and keep Day 4 as a full rest day."
}
```

## Operational Notes

- Set `DATABASE_URL` to change the database location; the default is SQLite at `./fitbuddy.db`.
- Set `GOOGLE_API_KEY` for live Gemini use.
- Keep API keys out of source control.
- The README explicitly positions FitBuddy as wellness guidance rather than a medical diagnostic or treatment system.

---

**Project basis:** This document is derived from the supplied FitBuddy source package, including its README, FastAPI routes, SQLAlchemy models, Jinja2 templates, CSS, and tests.
