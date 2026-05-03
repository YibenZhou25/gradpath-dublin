# Rubric: STAR Answer Quality Assessment

## Purpose

This rubric is invoked when the user asks the assistant to evaluate a behavioural
interview answer they have drafted. It scores the answer against the STAR format
expectations of Dublin tech employers.

## Scope

- **Applies to**: candidate-drafted answers to behavioural / situational interview
  questions
- **Does not apply to**: technical answers, system design walkthroughs, or "tell me
  about yourself" intro answers (different rubric)

## The four STAR pillars (total 100 points)

### Pillar S — Situation framing (15 points)

The candidate sets up the context in which the story took place.

- **13-15**: Concise (under 60 seconds spoken), specific (named timeframe,
  setting, scale), no irrelevant detail.
- **9-12**: Mostly concise, but a few sentences of context could be cut without
  loss of meaning.
- **5-8**: Excessive setup. Spent 2+ minutes establishing context before getting
  to the point.
- **0-4**: Either no context (story drops the listener cold) or rambling
  context that obscures the story.

Common failure: starting with "So basically I was at university and we had this
project and the professor said..." when "During my MSc thesis project last
spring..." conveys the same information in 8 words.

### Pillar T — Task articulation (15 points)

What specifically did the candidate need to do? What problem were they solving?

- **13-15**: Task is stated clearly, includes what success would look like, and
  acknowledges any constraints or stakes.
- **9-12**: Task is clear but lacks detail on what success looked like or what
  was at stake.
- **5-8**: Task is described but vaguely — "we had to build a thing".
- **0-4**: Task is fused into the action, never named separately. The listener
  doesn't know what challenge was being solved.

### Pillar A — Action specificity (50 points)

This is the core of the answer and must dominate the time. What did the
candidate do?

- **44-50**: Detailed, sequential actions. Uses "I" not "we" for personal
  contributions. Includes decisions made, options weighed, things tried that
  didn't work. Speaks to thought process, not just steps.
- **30-43**: Actions are described but mostly as outcomes ("I implemented X")
  without the reasoning behind decisions.
- **15-29**: Actions are vague ("I worked on it", "I helped the team") or
  consist mostly of "we" without individual contribution being clear.
- **0-14**: Action section is short, generic, or fully replaced with a passive
  description of what happened.

**Critical sub-signals**:
- Use of "I" vs "we" — at least 80% of action statements should be "I"
- Decisions described — interviewers want to see judgement, not just execution
- Failures within the action — "I tried X, it didn't work because Y, so I
  switched to Z" is much stronger than a clean march to success
- Specifics — names of tools, sizes of datasets, number of teammates,
  durations all signal real experience

### Pillar R — Result and reflection (20 points)

What was the outcome, and what did the candidate learn?

- **18-20**: Outcome is stated with measurable details (numbers, percentages,
  user feedback). Reflection identifies a lasting change in how the candidate
  works or thinks.
- **13-17**: Outcome is stated but qualitative or vague. Reflection is generic
  ("I learned the importance of teamwork").
- **7-12**: Outcome is barely mentioned. Story trails off.
- **0-6**: No result or no reflection. Story has no point that the listener can
  take away.

**Critical sub-signal**: stories where the result is "we shipped it and
everyone was happy" with no specifics or lessons read as either fabricated or
shallow.

## Output structure

When the assistant evaluates an answer, it should produce:

1. **Sub-scores** for S, T, A, R with brief justification
2. **Total score** out of 100
3. **The single most important fix** the candidate should make
4. **A rewritten section** demonstrating the fix (only one section, not the
   whole answer — keep advice focused)

## Common failure patterns the assistant should recognise

### Pattern 1: We-narration

Candidate uses "we" throughout the action section, making individual contribution
invisible. **Fix**: rewrite using "I" wherever the candidate personally did
something. The team frame is fine for context, but the action section needs
personal accountability.

### Pattern 2: Front-loaded context

Candidate spends 70% of the answer on situation/task. **Fix**: cut situation to
2 sentences max. Move the rest of the time to action.

### Pattern 3: Missing the messy middle

Candidate jumps from task to a clean successful action. No mention of dead-ends,
trade-offs, or revised plans. **Fix**: behavioural answers benefit from honest
inclusion of what didn't work first. Interviewers know real projects are messy
and read clean stories as polished but shallow.

### Pattern 4: Generic reflection

"I learned the importance of communication" or "I learned that teamwork
matters". **Fix**: name a specific change in behaviour. "Now whenever I start a
group project, I draft a one-page scope doc in week one — I learned this from
the X experience."

### Pattern 5: Modesty erasure (common for international students)

Candidate de-emphasises their own role due to cultural reluctance to claim
credit. The interviewer scores this as low individual contribution. **Fix**:
practise stating contributions plainly. "I designed the schema. I wrote the
authentication module. I led the integration testing." This is not bragging in
the Western interview context — it is the information the interviewer needs.

### Pattern 6: Plot-twist results

Candidate ends with a vague positive ("the project went well") without any
specifics. **Fix**: pick one or two metrics — performance number, user count,
grade received, peer feedback — and state them.

## Coaching tone

The assistant should:
- Be honest about what is weak in the answer
- Pair every criticism with a concrete fix
- Avoid generic encouragement ("great answer!") that doesn't help
- Refer to specific phrases or sentences in the candidate's draft when
  identifying issues

The assistant should NOT:
- Rewrite the entire answer for the user (this is their interview, not the
  assistant's)
- Insert specific factual claims that weren't in the candidate's original
  (e.g. inventing a metric)
- Give advice that contradicts the cultural-interview-norms file in
  `05_cultural/`

---

*This rubric is a curated working tool. It is not external authoritative guidance.*
