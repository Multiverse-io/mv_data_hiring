# mv_data_hiring — Repo-Specific BugBot Rules

> Org-wide rules are enforced via Cursor Team Rules.

## Hiring Test Repository

- This repo contains take-home tests for data engineering candidates. Changes to task descriptions (`TASK.md`), API behaviour, or test data directly affect the candidate experience — review for clarity and fairness.
- The API credentials in `app.py` (`USERNAME`, `PASSWORD`) are intentionally hardcoded for the test environment. These are not production secrets — do not flag them as security issues.

## API Structure

- The FastAPI app in `data_engineering_test_api/app.py` serves CSV data via paginated, authenticated endpoints. Pydantic models in `models.py` define the response schemas.
- Pagination uses encrypted tokens (Fernet). The encryption key is generated at startup and is ephemeral — do not persist or share it.
- Test data lives in `data_engineering_test_api/data/*.csv`. Changes to CSV schema must be reflected in both the Pydantic models and the task description.

## Candidate-Facing Concerns

- The `TASK.md` and `README.md` are read by candidates. Keep instructions clear, self-contained, and free of internal jargon.
- Do not add dependencies or complexity to the API that isn't relevant to the test — the API should remain simple enough for candidates to understand quickly.
