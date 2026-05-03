# Rubric: CV Scoring for Graduate Software Engineering Roles in Ireland

## Purpose

This rubric is invoked when the assistant is asked to evaluate or score a user's CV
against the bar set by graduate / junior software engineering roles at Dublin tech
employers. It is calibrated to the patterns observed across the company profiles in
the knowledge base.

## Scope

- **Applies to**: graduate-level Software Engineering, Junior Developer, Junior Data
  Engineer, Junior ML Engineer CVs
- **Does not apply to**: senior CVs, manager CVs, non-technical CVs

## Scoring dimensions (total 100 points)

### Dimension A — Technical Skill Evidence (35 points)

What is being measured: are the technical skills claimed in the CV substantiated
with evidence the reader can verify or reason about?

- **30-35**: Each major skill is tied to a specific project, internship, or coursework
  with measurable scope. A reader can tell what the candidate actually did with each tool.
- **20-29**: Skills are present and most are tied to context, but some appear as a
  bare list with no supporting evidence.
- **10-19**: Skills are claimed but mostly as a list. The reader cannot verify
  whether the candidate has practical experience or only academic exposure.
- **0-9**: Skills section is generic, copied from job-description language, or absent.

Specific signals to look for:
- A "skills" list containing 15+ technologies is a yellow flag — reads as
  unfocused or padded
- Languages without context ("Java, Python, C++, Go, Rust") suggest exam-only exposure
- Strong CVs name the language/framework alongside the project that used it

### Dimension B — Project Evidence (25 points)

What is being measured: does the CV demonstrate substantive project work beyond
coursework deliverables?

- **22-25**: At least 2 substantial projects beyond standard coursework, each with
  clearly stated scope, measurable outcome, and a link to GitHub or live demo.
- **15-21**: 1-2 strong projects, but missing either outcome metrics or a public
  link to verify the work.
- **8-14**: Projects are listed but described in vague terms ("worked on a system
  for...") with no scope or outcome.
- **0-7**: Only standard coursework, no independent projects, or no projects at all.

Specific signals to look for:
- Each project should answer: what problem? what tech? what was your specific
  contribution? what was the outcome?
- Projects without GitHub links are weaker — recruiters cannot verify the work
- Projects with screenshots or live demos significantly outperform text-only descriptions

### Dimension C — Education & Degree Fit (15 points)

What is being measured: does the academic record clearly support the target role?

- **13-15**: Degree, classification (where applicable), and relevant modules are
  clearly stated. Specialisation matches target roles.
- **9-12**: Degree clear but classification missing, or relevant coursework not
  highlighted.
- **5-8**: Education section is bare-bones, requires the reader to infer relevance.
- **0-4**: Critical information missing, or degree poorly aligned to target role
  with no compensating evidence.

### Dimension D — Communication & STAR-readiness (10 points)

What is being measured: can each bullet point on this CV be expanded into a strong
behavioural answer?

- **9-10**: Bullets are written in a STAR-friendly way: action verb, what was done,
  measurable outcome.
- **6-8**: Most bullets describe actions but lack outcomes; behavioural-friendly with effort.
- **3-5**: Bullets describe responsibilities rather than achievements ("responsible
  for the front-end team")
- **0-2**: Bullets are generic, vague, or read as job-description language.

Specific signals to look for:
- Strong CVs use action verbs: "designed", "built", "reduced", "automated"
- Weak CVs use passive language: "was involved in", "responsible for", "helped with"
- Numbers in bullets are nearly always a positive signal

### Dimension E — Work Authorisation Clarity (15 points)

What is being measured: is the candidate's right to work in Ireland made explicit?

- **13-15**: Clear, concise statement of work authorisation status (e.g. "Eligible
  to work in Ireland under Stamp 1G post-study graduate visa until [date]")
- **6-12**: Mentioned but unclear or buried in the cover letter rather than CV
- **0-5**: Not stated. This is a critical CV defect for non-EU graduates in Ireland —
  many ATS filters and recruiters will deprioritise CVs without clear work
  authorisation.

This dimension is weighted heavily because lack of work-authorisation clarity is
the single most common preventable cause of silent CV rejection for international
graduates.

## How the assistant should report scores

When applying this rubric:

1. Compute a sub-score for each of the five dimensions
2. Sum to a total /100
3. Provide a 1-2 sentence justification per dimension, citing specific text from
   the user's CV
4. Identify the **top 3 highest-leverage improvements** the user could make
5. Be candid but constructive — vague encouragement does not help the user

## Common failure modes specific to international students

- **Skills wall**: long unstructured skills list, often translated literally from
  Chinese-style CV conventions
- **Project list overload**: listing every coursework project equally rather than
  curating to the strongest 2-3
- **Missing Stamp / authorisation line**: especially common for students writing
  their first English-language CV
- **Pronoun-free bullets**: bullets that omit "I" entirely make individual
  contribution invisible
- **Over-translation of academic honours**: scholarship details that don't translate
  meaningfully to Irish recruiters often clutter the page

## How the assistant should NOT use this rubric

- It is not a hiring decision. Real recruiters apply different and often opaque
  criteria, and human judgement at every employer varies.
- It should not be used to compare two users to each other.
- It should always be presented to the user with the breakdown shown — not just
  a single number.

---

*This rubric is a curated working tool. It is not external authoritative guidance.*
