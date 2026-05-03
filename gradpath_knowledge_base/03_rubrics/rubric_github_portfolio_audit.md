# Rubric: GitHub Portfolio Audit for Graduate SWE Applications

## Purpose

This rubric guides the assistant when auditing a user's public GitHub profile to
assess whether their portfolio supports the technical claims on their CV. It is
applied after the GitHub API has retrieved the user's public repositories,
their READMEs, and basic activity metadata.

## Scope

- **Applies to**: candidates targeting graduate / junior SWE, Data Engineer, ML
  Engineer roles where a public portfolio is a meaningful signal
- **Does not apply to**: candidates whose strongest evidence is non-public (e.g.
  industrial internships, work product behind paywalls)

## The five dimensions of portfolio strength (total 100 points)

### Dimension A — Pinned repository quality (25 points)

GitHub allows users to "pin" up to 6 repositories to the top of their profile.
These are the first thing recruiters see.

- **22-25**: 4-6 pinned repos, each with a clear purpose, working code, and a
  README that explains what the project does, how to run it, and what the
  candidate's specific contribution was.
- **15-21**: 3-4 pinned repos, mostly well-described, but at least one feels
  unfinished or unclear in purpose.
- **8-14**: Pinned repos exist but READMEs are minimal (<100 words), or pins
  include forks/cloned tutorials with no original work.
- **0-7**: No pins, or pins that hurt the candidate (empty repos, abandoned
  projects, irrelevant content).

**Critical signal for graduates**: pinned repos should be a curated portfolio,
not a random sample. The user should pin their strongest, most-relevant work.

### Dimension B — README quality (25 points)

For each substantive repo, the README should answer four questions in the first
500 words:
1. What does this project do?
2. Why does it exist? (problem solved or motivation)
3. How do you run it?
4. What did the author specifically contribute? (especially for group projects)

- **22-25**: At least 2 repos have READMEs answering all four questions, with
  screenshots or example output, and clear sections.
- **15-21**: READMEs answer most questions but lack screenshots, structure, or
  specific contribution attribution.
- **8-14**: READMEs are short and skeletal — mostly title + one-line description
  + maybe install instructions.
- **0-7**: READMEs missing entirely, or contain only the auto-generated default
  text.

**For Chinese students particularly**: READMEs in Chinese reduce accessibility
to Irish recruiters. Either translate, or include a parallel English version.

### Dimension C — Tech stack alignment with CV claims (20 points)

Compare the languages and frameworks visible in pinned repos to the skills
claimed on the CV.

- **18-20**: Every major skill claimed on the CV is visibly used in at least one
  pinned repo.
- **12-17**: Most CV skills are visible, but 1-2 important claims have no
  GitHub evidence.
- **6-11**: Significant gaps — multiple CV claims have no portfolio backing.
- **0-5**: CV and GitHub appear to belong to different people. CV claims
  proficiency in technologies that don't appear at all in the visible work.

### Dimension D — Activity recency and pattern (15 points)

GitHub's contribution graph is publicly visible and recruiters do look at it.

- **13-15**: Regular contributions over the past 12 months. No long gaps, several
  recent commits.
- **9-12**: Mostly active, but with one notable gap (e.g. all activity 6+ months
  ago).
- **5-8**: Activity heavily clustered around coursework deadlines, large gaps
  otherwise.
- **0-4**: Profile appears abandoned. No commits in 6+ months. Reads as "I made
  this account for the application".

**Important context**: a sparse contribution graph is not automatically bad. A
student doing private work or working in a non-Git environment may have weak
public activity. The audit should mention this caveat to the user rather than
penalising heavily.

### Dimension E — Originality and substance (15 points)

What proportion of the user's visible work is genuinely original vs. tutorial
follow-along, course assignments left as-is, or forks of other projects?

- **13-15**: Strong original work clearly visible. Original problem framing,
  not a copy of a tutorial.
- **9-12**: Mostly original but mixed with some tutorial-pattern repos.
- **5-8**: Heavy presence of "I followed a tutorial" repos with no extension or
  personalisation.
- **0-4**: Profile is dominated by clones, forks, and bare assignment submissions.

## Output structure

When the assistant produces a portfolio audit, it should output:

1. **Overall score** out of 100, with sub-scores per dimension
2. **Top 3 strengths** — what's working
3. **Top 3 leverage improvements** — ranked by impact, with concrete actions
4. **Specific repo-by-repo callouts** for the pinned repositories

A typical "leverage improvement" looks like:

> *Improvement #1: Strengthen the README of `ml-recommender-system`.*
> Currently this repo has a 2-line README. As your most relevant project for
> data/ML roles, it should explain (a) the dataset, (b) the model architecture,
> (c) the evaluation results with metrics, (d) how to reproduce. Estimated time:
> 30 minutes. Estimated impact: high — this is likely your portfolio's centrepiece.

## Common patterns the assistant should recognise

### Pattern 1: The empty profile

User has 0-2 public repos, both small. Recommendation: pick the strongest course
project, polish its README, pin it. Even one well-presented repo beats a void.

### Pattern 2: The course-dump profile

User has 15+ repos, all named like `cs101-assignment-3` or `final-project`.
Recommendation: archive or hide the bulk; pin the 3-4 strongest, rename them
descriptively, polish their READMEs.

### Pattern 3: The strong-but-hidden profile

User has substantive work but everything is private (work projects),
unfinished, or buried beneath forks. Recommendation: extract the public-shareable
parts; create one or two clean public repos that demonstrate the relevant
skills.

### Pattern 4: The portfolio-style profile

User already has a curated profile with clear pins, strong READMEs, and recent
activity. Recommendation: minor polish only. The assistant should affirm rather
than over-coach.

## How the assistant should NOT use this rubric

- It is not the only signal that matters. Many strong candidates have weak
  GitHub profiles for legitimate reasons (industrial internships, private work,
  non-engineering primary specialisation).
- It should be presented to the user as constructive guidance, not a verdict.
- Scores should always be paired with specific, actionable next steps. A
  numeric score without action items is useless.

---

*This rubric is a curated working tool. It is not external authoritative guidance.*
