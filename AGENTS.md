# AGENTS.md

Guidance for coding agents and automated review in this repository.
<!-- Template: add build, test and convention notes for agents above the review rules. -->

## Code Review Rules

These rules guide automated pull request review and apply to human reviewers too.
An `AGENTS.md` in a subdirectory can add rules for that directory; they apply on top of these.

<!-- Template: keep the shared rules below as they are. Fill in the slots marked "Team:",
     then delete each slot's comment. Leaving a slot empty is safe: the shared rules still work. -->

### What counts as serious (P0/P1)

Comment only on problems that would cause real harm if this change merged:

- Wrong behaviour: logic errors, unhandled errors or edge cases, race conditions, data loss or corruption.
- Security: missing authentication or authorisation checks, injection, unsafe deserialisation,
  secrets or credentials in code, config or logs.
- Personal data: new logging, storage, export or third-party transfer of personal data, or
  weaker protection of data that is already held.
- Breaking changes: public APIs, events and message schemas, or database migrations that are not
  backwards compatible or cannot be rolled back.
- Access: changes that widen who or what can reach a system (IAM, network rules, repository or
  pipeline permissions).
- Missing or weakened tests for changed behaviour, where a regression would be hard to notice.

### What not to comment on

- Style, formatting, naming and import order. Linters and formatters own these.
- Alternative designs or personal preferences when the change is correct.
- Anything an earlier review comment on this pull request already raised.
- Generated, lock and vendored files (below), except to flag a secret or a change made by hand
  to a file that should be generated.

### Paths to skip

- Lockfiles: `package-lock.json`, `yarn.lock`, `pnpm-lock.yaml`, `mix.lock`, `poetry.lock`,
  `uv.lock`, `Gemfile.lock`, `go.sum`, `.terraform.lock.hcl`
- Generated output: `dist/`, `build/`, `coverage/`, `*.min.js`, `*.generated.*`, `*.snap`
- Vendored or installed code: `vendor/`, `third_party/`, `deps/`, `node_modules/`
<!-- Team: add this repository's own generated or vendored paths, for example an OpenAPI client
     directory or a schema dump. -->

### How to comment

- One issue per comment, on the line that causes it.
- First sentence: the problem and what goes wrong because of it. Then the fix, as a suggestion
  block when it is small.
- No praise, no summary of the change, no restating the diff.
- If you are not sure it is a bug, say what would confirm it instead of asserting it.

### This repository's conventions

Follow the conventions in this repository's `README.md`, `CONTRIBUTING.md` and any nested
`AGENTS.md`, and flag changes that break them.
<!-- Team: link the documents that define how this repository works (architecture notes, ADRs,
     testing guide). Then add the rules a reviewer must enforce here, one line each, saying what to
     flag and why. For example:
     - Every account state change goes through `Accounts.State.Transitions`. Flag direct writes
       to the `state` field, because they skip the transition checks. -->

### Rules carried over from BugBot

<!-- Moved from .cursor/BUGBOT.md on 2026-11-18. Edit freely; the old file has been removed. -->

#### Hiring Test Repository

- This repo contains take-home tests for data engineering candidates. Changes to task descriptions (`TASK.md`), API behaviour, or test data directly affect the candidate experience — review for clarity and fairness.
- The API credentials in `app.py` (`USERNAME`, `PASSWORD`) are intentionally hardcoded for the test environment. These are not production secrets — do not flag them as security issues.

#### API Structure

- The FastAPI app in `data_engineering_test_api/app.py` serves CSV data via paginated, authenticated endpoints. Pydantic models in `models.py` define the response schemas.
- Pagination uses encrypted tokens (Fernet). The encryption key is generated at startup and is ephemeral — do not persist or share it.
- Test data lives in `data_engineering_test_api/data/*.csv`. Changes to CSV schema must be reflected in both the Pydantic models and the task description.

#### Candidate-Facing Concerns

- The `TASK.md` and `README.md` are read by candidates. Keep instructions clear, self-contained, and free of internal jargon.
- Do not add dependencies or complexity to the API that isn't relevant to the test — the API should remain simple enough for candidates to understand quickly.

### Look closely at

<!-- Team: list the paths where any change needs extra care, for example authentication,
     billing, migrations or infrastructure, with one line on why. -->
