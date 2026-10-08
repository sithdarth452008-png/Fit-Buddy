# Project Testing

## FitBuddy — Test Strategy, Current Test Cases, Expected Outcomes, and Quality Checks

## Testing Strategy

The supplied test suite uses FastAPI TestClient and exercises the application through HTTP-level behavior. This is appropriate for verifying that routing, template rendering, service calls, persistence, and response structures work together.

## Implemented Tests

- **test_home_page:** Verifies the home page returns HTTP 200 and contains the FitBuddy brand.
- **test_health:** Verifies the health endpoint returns HTTP 200 and `status='ok'`.
- **test_generate_api:** Posts a valid user profile and checks for a successful response, user ID, workout plan, and nutrition tip.
- **test_feedback_api:** Submits feedback for the generated test user and checks that an updated plan is returned.

## Additional Recommended Tests

- Reject age below 13 or above 100.
- Reject weight outside the configured range.
- Reject unsupported intensity or experience values.
- Reject blank/too-short user IDs and feedback.
- Submit feedback for an unknown user and verify HTTP 404.
- Verify deleting a user removes associated plans.
- Verify `/api/users` returns stored profile fields.
- Verify Gemini fallback output is available when no API key is configured.
- Verify repeated user IDs update the existing profile rather than creating duplicate users.

## Manual UI Test Cases

### TC-01 Generate Plan

Enter valid profile data, submit the form, and verify the result page displays profile details, workout plan, and nutrition/recovery tip.

### TC-02 Feedback Update

Enter a request such as adding more cardio or another rest day. Verify the page indicates that the plan was updated and displays the revised plan.

### TC-03 Admin Dashboard

Open `/view-all-users` and verify the stored profile and plan appear.

### TC-04 Delete

Use the dashboard Delete action and verify the user no longer appears.

## Acceptance Criteria

- All supplied automated tests pass.
- Invalid input is rejected without creating invalid records.
- Valid generation produces both workout and nutrition outputs.
- Feedback updates an existing plan rather than creating an unrelated user.
- Admin operations do not expose application errors during normal use.
- The app can be demonstrated locally using fallback behavior when Gemini is not configured.

## Quick Reference

| Test | Expected Result |
|---|---|
| Home page | 200 + FitBuddy text |
| Health | 200 + status ok |
| Generate API | 200 + `workout_plan` + `nutrition_tip` |
| Feedback API | 200 + `updated_plan` |
| Invalid input | Validation error / rejected request |
| Unknown feedback user | 404 |

---

**Project basis:** This document is derived from the supplied FitBuddy source package, including its README, FastAPI routes, SQLAlchemy models, Jinja2 templates, CSS, and tests.
