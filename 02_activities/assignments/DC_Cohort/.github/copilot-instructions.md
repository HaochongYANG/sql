# Copilot workspace instructions (DC_Cohort SQL assignments)

## What this repo is
This folder contains **two SQL assignments** (prompts + rubrics) for a SQLite database (`farmersmarket.db`). You will mostly edit:
- `Assignment1.md` and `assignment1.sql`
- `Assignment2.md` and `assignment2.sql`

The database file is not stored in this folder. Queries are expected to run in **DB Browser for SQLite** (or `sqlite3`) using **SQLite syntax**.

## Hard requirements / guardrails
- **Do not write the ethics responses for the student.**
  - Both assignments include a Section 4 ethics writeup requirement and rubrics explicitly note it should not be written by an LLM.
  - You *may* help with: outlining, brainstorming topics, tightening wording the user already wrote, grammar fixes, and rubric checks.
  - You *must not* generate a full 250–1000 word response.
- Preserve the assignment prompt text and headings; only add content where the student is supposed to respond.
- In `.sql` files, write answers **only between** the `--QUERY n` and `--END QUERY` markers.

## SQL dialect and style
- Assume **SQLite**:
  - Dates: `STRFTIME('%m', col)`, `STRFTIME('%Y', col)` return strings.
  - String concat: use `||`.
  - Temp tables: `CREATE TEMP TABLE ...`.
- Prefer readable formatting:
  - Uppercase SQL keywords (`SELECT`, `FROM`, `WHERE`, `GROUP BY`, …)
  - One column per line for long `SELECT` lists.
  - Use table aliases for joins (`vendor AS v`).
- Only include `LIMIT` when the prompt asks for it.

## How to help effectively
When asked to solve a question:
1. Restate the specific prompt (e.g., “Assignment 2 → Windowed Functions Q2”).
2. Produce the minimal SQLite query that matches the requirement.
3. Explain any SQLite gotchas (e.g., `STRFTIME` outputs strings; sort vs filter; `HAVING` vs `WHERE`).
4. If the prompt expects a particular output ordering, include `ORDER BY`.

## Common SQLite gotchas in these assignments
- `BETWEEN` is inclusive.
- `LIKE` is case-insensitive for ASCII by default in SQLite, but prefer `LOWER(col) LIKE '%x%'` when the prompt says “regardless of capitalization”.
- `REGEXP` is **not built-in** to SQLite. If the environment doesn’t support it, explain the limitation and provide a closest SQLite-native alternative (`GLOB`, `LIKE`, or `WHERE col GLOB '*[0-9]*'`) *unless the course tooling explicitly provides `REGEXP`*.

## “Link, don’t embed” references
- Assignment prompts and requirements live in:
  - `Assignment1.md` and `Assignment1_rubric.md`
  - `Assignment2.md` and `Assignment2_rubric.md`
- When providing guidance, reference those files rather than duplicating large prompt text.
