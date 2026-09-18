# Evidence — requirements-gap-check

**Tested on:** Windows PowerShell · Python `py` · Date: 2026-09-19

---

## 1. It fired when it should

### Test 1 — Missing requirements

**What I typed:**

```text
The assignment requires a report, three sources, a conclusion, and validation. My work has the report and three sources. What haven't I covered?
```

**What happened:**

```text
ROUTED  requirements-gap-check

### Missing
- **Requirement:** Conclusion
  **Evidence:** You did not mention including a conclusion in your work.

- **Requirement:** Validation
  **Evidence:** There is no mention or evidence of validation in your work.

### Met
- **Requirement:** Report
  **Evidence:** You stated that your work includes the report.

- **Requirement:** Three sources
  **Evidence:** You stated that your work includes three sources.
```

**Did it activate on its own?** Yes.

---

### Test 2 — Partial requirements

**What I typed:**

```text
Requirements: Provide results with figures or tables; Include a bibliography; Use APA citations. ===SUBMISSION=== The results section contains observations but no figures or tables. There is no bibliography, and the citations are inconsistent. What requirements are missing or only partially covered?
```

**What happened:**

```text
ROUTED  requirements-gap-check

### Missing
- **Requirement:** Include a bibliography
  **Evidence:** The submission explicitly states there is no bibliography.

### Partial
- **Requirement:** Provide results with figures or tables
  **Evidence:** The results section contains observations but no figures or tables,
  so this requirement is only partially covered.

- **Requirement:** Use APA citations
  **Evidence:** The citations are inconsistent, indicating partial coverage.

No other requirements were identified as missing or unverifiable.
```

**Did it activate on its own?** Yes.

---

### Test 3 — Requirements and work described directly

**What I typed:**

```text
I have an assignment brief that says I need a SKILL.md, meta.yml, EVIDENCE.md, and a Python script. I created SKILL.md and the Python script, but I haven't created meta.yml or EVIDENCE.md. What requirements am I missing?
```

**What happened:**

```text
ROUTED  requirements-gap-check

### Missing
- **Requirement:** meta.yml file
  **Evidence:** You have not created or provided the meta.yml file.

- **Requirement:** EVIDENCE.md file
  **Evidence:** You have not created or provided the EVIDENCE.md file.

### Met
- **Requirement:** SKILL.md file
  **Evidence:** You have created the SKILL.md file.

- **Requirement:** Python script
  **Evidence:** You have created the Python script.
```

**Did it activate on its own?** Yes.

---

## 2. It stayed quiet when it should

### Near-miss 1 — Rewrite request

**What I typed:**

```text
Rewrite my assignment so that it sounds more professional and polished.
```

**What happened:**

```text
ROUTED  NO_SKILL — answering directly
```

**Did it stay dormant?** Yes.

**Why this one is a real test:** It concerns an assignment, but asks for rewriting rather than checking whether requirements are covered.

---

### Near-miss 2 — Create missing artifact

**What I typed:**

```text
Write the missing EVIDENCE.md file for my assignment.
```

**What happened:**

```text
ROUTED  NO_SKILL — answering directly
```

**Did it stay dormant?** Yes.

**Why this one is a real test:** It refers to something missing from an assignment, but asks the system to create the missing artifact rather than identify requirements gaps.

---

### Boundary test — Grading

**What I typed:**

```text
Grade my assignment from 1 to 10 and tell me what score it deserves.
```

**What happened:**

```text
ROUTED  lab-grader
```

**Did requirements-gap-check stay dormant?** Yes.

**Why this one is a real test:** Grading is related to evaluating an assignment, but it is a different task from identifying uncovered requirements.

---

### Near-miss 3 — Explain the brief

**What I typed:**

```text
Explain this assignment brief to me in simple terms. It requires a report, bibliography, results section, and APA citations.
```

**What happened:**

```text
ROUTED  jhf-brief
```

**Did requirements-gap-check stay dormant?** Yes.

**Why this one is a real test:** The request contains assignment requirements but does not provide the user's work or ask for a gap comparison.

---

## 3. What it cost

The final successful requirements-gap-check runs reported:

```text
menu shown to the router .... ~731 tokens

we actually loaded .......... ~1,094 tokens (requirements-gap-check)

SAVED ....................... ~2,052 tokens
```

This demonstrates progressive disclosure: the requirements-gap-check skill body was loaded after routing, while the other skills remained unloaded.

---

## 4. Anything a reviewer should know

* **Known limitation:** The skill needs both the assignment requirements and enough information about the user's work to make a meaningful comparison.

* **Needs an API key / network:** No for the deterministic `requirements_gap_checker.py` script.

* **Anything that surprised you:** The router initially failed to activate on some natural wording such as "What haven't I covered?" even though the request clearly described requirements and work. The router prompt was strengthened with explicit natural trigger examples, after which the same type of request routed to `requirements-gap-check`.
