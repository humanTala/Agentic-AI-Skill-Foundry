
---
name: requirements-gap-check
description: >
  Use when the user provides or describes BOTH assignment requirements
  (brief, instructions, rubric, specification, or checklist) AND their own
  work, draft, submission, or implementation, and asks what they missed,
  what they have not covered, what is still uncovered, what requirements are
  missing, incomplete, partially satisfied, or unmet, or whether their work
  covers the stated requirements. Typical requests include "what am I
  missing?", "did I miss anything?", "what haven't I covered?", "what have
  I not covered?", "what is still uncovered?", "which requirements are
  missing?", and "does my work cover the requirements". Does NOT fire on
  grading, scoring, or rubric evaluation; rewriting, improving, or
  proofreading; explaining or summarizing a brief without the user's work;
  or creating/writing missing assignment content.
---

# Requirements Gap Check

Compares assignment requirements with the user's own work and reports which
requirements are met, partially covered, missing, or cannot be verified.

## When to use this

Fires when the user asks to:

- identify what requirements they are missing from an assignment brief
- compare their submission or implementation against stated requirements
- find what they have not covered or what is still uncovered
- identify requirements that are only partially satisfied
- check whether their work covers the requirements in a brief or specification

**Does NOT fire on:**

- grading, scoring, marking, or rubric evaluation — those are assessment tasks
- rewriting or improving the user's work — those are editing tasks
- explaining or summarizing an assignment brief without the user's work
- proofreading for grammar or surface errors
- writing missing sections, files, code, or other assignment content

## Steps

1. Identify the assignment requirements and the user's work.
2. Extract the individual requirements from the brief without inventing new
   requirements.
3. Compare each requirement against the supplied work.
4. Classify each requirement as Met, Partial, Missing, or Can't verify.
5. Report the gaps first, followed by the requirements that are already met.

## Rules

- Do not invent requirements that are not stated or reasonably implied by the
  supplied brief.
- Do not give grades, scores, rankings, or overall quality judgments.
- Do not rewrite or create missing assignment content unless the user
  separately asks for that after the gap analysis.
- Do not claim that a requirement is satisfied without evidence in the
  supplied work.
- Distinguish Partial from Missing.
- Distinguish Missing from Can't verify.
- Report only what can be supported by the supplied requirements and work.
- The deterministic gap-classification logic is implemented in
  `scripts/requirements_gap_checker.py`.

## Scripts

| Script | What it does |
|---|---|
| `scripts/requirements_gap_checker.py` | Extracts requirements and compares them against the supplied submission using deterministic gap-detection logic. |
