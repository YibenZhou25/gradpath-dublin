# Rubric: Extracting Required Skills from a Job Description

## Purpose

This rubric guides the assistant when it needs to parse a job description (JD) and
extract a structured list of required and preferred skills. The output of this
process feeds directly into the CV-to-JD matching computation in the code-interpreter
layer.

## Scope

- **Applies to**: graduate / junior / entry-level technical job descriptions
- **Does not apply to**: senior or executive JDs (different expectation patterns)

## Three skill categories to extract

For every JD, build three separate lists:

### Category 1 — Hard requirements (must-have)

Signals that something is a hard requirement:
- Phrasing: "required", "must have", "minimum qualifications", "essential"
- Listed under a heading like "Requirements" or "Qualifications"
- Mentioned 2+ times across the JD

Examples:
- "Bachelor's degree in Computer Science or related field" → Hard requirement
- "Proficient in at least one of: Java, Python, Go" → Hard requirement (with
  flexibility)
- "Experience with relational databases" → Hard requirement

### Category 2 — Preferred skills (nice-to-have)

Signals that something is preferred but not required:
- Phrasing: "preferred", "nice to have", "bonus", "a plus", "ideally"
- Listed under "Preferred qualifications" or "Bonus skills"
- Mentioned only once, often near the end of the requirements section

Examples:
- "Familiarity with AWS or GCP a plus" → Preferred
- "Open-source contributions are a bonus" → Preferred
- "Prior experience with React preferred but not required" → Preferred

### Category 3 — Implicit signals (read between the lines)

These are not in the requirements list but matter for the CV-match score:
- Tech stack mentioned in "About the team" or "What you'll do" sections
- Methodologies mentioned in "How we work" sections (e.g. "we use TDD", "we ship
  daily")
- Soft skills mentioned in culture sections (e.g. "ownership", "writing-heavy")

These are valuable because:
- They reveal the day-to-day reality of the role
- They give CV-tailoring clues even when not formal requirements
- They distinguish between two JDs with identical requirement lists

## Skill normalisation

Different JDs use different terms for the same skill. Normalise to canonical names:

| Variants seen in JDs | Canonical form |
|---------------------|----------------|
| "JavaScript", "JS", "ES6", "Node.js" (when referring to language) | JavaScript |
| "TypeScript", "TS" | TypeScript |
| "ReactJS", "React.js", "React" | React |
| "AWS", "Amazon Web Services" | AWS |
| "GCP", "Google Cloud Platform", "Google Cloud" | GCP |
| "K8s", "Kubernetes" | Kubernetes |
| "CI/CD", "continuous integration", "continuous deployment" | CI/CD |
| "OOP", "object-oriented programming" | Object-oriented programming |
| "REST", "RESTful", "REST API" | REST APIs |
| "ML", "machine learning" | Machine learning |
| "SQL" | SQL (do not collapse with specific databases) |
| "PostgreSQL", "Postgres" | PostgreSQL |

This normalisation is essential for CV-match scoring — a CV mentioning "Postgres"
should match a JD requiring "PostgreSQL".

## Output structure

For each JD, produce a JSON-shaped output:

```json
{
  "role_title": "Graduate Software Engineer",
  "company": "...",
  "location": "Dublin, Ireland",
  "hard_requirements": [
    {"skill": "Java", "evidence_phrase": "Proficient in Java required"},
    {"skill": "SQL", "evidence_phrase": "Experience with relational databases"},
    ...
  ],
  "preferred_skills": [
    {"skill": "Kubernetes", "evidence_phrase": "Familiarity with K8s a plus"},
    ...
  ],
  "implicit_signals": [
    {"signal": "TDD culture", "evidence_phrase": "We follow test-driven development"},
    {"signal": "Code review heavy", "evidence_phrase": "All changes require review"},
    ...
  ],
  "qualifications": {
    "degree": "Bachelor's in CS or related",
    "experience_years": 0,
    "work_authorisation": "Must have right to work in Ireland"
  },
  "compensation_stated": null,
  "working_model": "Hybrid - 3 days in office"
}
```

## Edge cases the assistant must handle

### Edge case 1: JD lists no specific languages

Some JDs say only "experience with at least one modern programming language".
Treat this as: hard requirement = "any modern language", and use the languages
mentioned in the "About the team" section as implicit signals for the team's
actual stack.

### Edge case 2: Stack laundry list

Some JDs list 15+ technologies without distinguishing requirements from preferences.
In this case:
- The first 3-5 listed are usually most important (recency bias of writers)
- Technologies tied to specific responsibilities ("you will work with X") are more
  important than technologies in undifferentiated lists

### Edge case 3: Soft skills as requirements

When "communication skills" or "collaboration" appears as a hard requirement,
extract it but note that this is not a verifiable hard skill and should be
treated as an implicit signal for the behavioural-interview assessment.

### Edge case 4: Inflated requirements

Junior JDs sometimes list 5+ years of experience as "required" — this is a
known pattern of poor JD writing. Note when this happens, but do not let it
disqualify a graduate from applying. The user should be advised that "5 years
required" on a graduate JD is often actually flexible.

## How this rubric feeds the matching computation

The hard requirements drive the **base match score** (40% of total).
Preferred skills drive the **bonus score** (15%).
Implicit signals drive the **CV-tailoring suggestions** (qualitative output, not numeric).

For details, see `rubric_cv_to_jd_matching.md` (related rubric in this folder).

---

*This rubric is a curated working tool. It is not external authoritative guidance.*
