# Rubric: [What is being scored]

> **Template instructions** (delete this block in finished file):
> A rubric is the assistant's internal "ruler". When the user asks for an evaluation
> (CV scoring, GitHub audit, STAR-answer quality), the assistant retrieves the
> relevant rubric via file search and applies it consistently.
> Target length: 400–700 tokens. Be concrete, not aspirational.

## Purpose

One sentence: *what does this rubric measure, and when should the assistant invoke it?*

## Scope

- **Applies to**: e.g. graduate-level Software Engineering CVs in the Irish market
- **Does not apply to**: e.g. senior-level CVs, non-technical CVs

## Scoring dimensions (total 100 points)

### Dimension A — [Name] ([X] points)

What is being measured:

Score breakdown:
- 90–100%: clear, specific, evidence-backed
- 70–89%: present but partially generic
- 40–69%: claimed but not substantiated
- 0–39%: missing or vague

Specific signals to look for:
-
-

Specific failure modes for non-native English speakers:
-

### Dimension B — [Name] ([X] points)

[same structure]

### Dimension C — [Name] ([X] points)

[same structure]

## How the assistant should report scores

When applying this rubric, the assistant should produce:

1. A numerical sub-score for each dimension
2. A short justification (1–2 sentences) per dimension citing the user's input
3. The top 3 highest-leverage improvements, ranked

## How the assistant should NOT use this rubric

- It should not be applied silently — always show the breakdown to the user.
- It is not a hiring decision. The assistant should remind the user that real
  recruiters apply different and often opaque criteria.
- It should not be used to compare two users to each other.

---

*File path: `03_rubrics/rubric_[topic].md`*

*Examples:*
- `rubric_cv_scoring.md`
- `rubric_jd_skill_extraction.md`
- `rubric_github_portfolio_audit.md`
- `rubric_star_answer_quality.md`
