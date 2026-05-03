# Software Engineering · Technical Interview Patterns

> Curated guidance on technical interview formats commonly used by Dublin tech employers
> for graduate / junior software engineering roles. Patterns are aggregated from
> publicly observable interview practices across the major Dublin tech employers
> profiled in this knowledge base.

## 1. The standard graduate SWE interview pipeline

Most Dublin tech employers (Stripe, Intercom, Datadog, Pinterest, Squarespace, MongoDB,
Twilio, Klaviyo) follow a similar 4-5 stage pipeline for graduate / junior software
engineers:

1. **Application screen** — automated CV parsing + recruiter review (1-3 days)
2. **Online assessment (OA)** — coding challenge on HackerRank / Codility / CoderPad
   (60-120 minutes, 2-3 problems)
3. **Phone screen with engineer** — 45-60 min, one coding problem + brief discussion
4. **Onsite / virtual onsite** — 3-4 rounds in a single day, including:
   - 2× coding interviews (LeetCode-medium difficulty)
   - 1× behavioural / values interview
   - 1× system design (only at some employers, usually scaled-down for grads)
5. **Team match / hiring committee** — internal review, offer extended

## 2. Coding round patterns

### What to expect at "LeetCode medium" difficulty

For graduate roles in Dublin, "medium" typically means:
- Array / string manipulation requiring O(n) thinking
- Hash maps for lookup optimisation
- Two pointers / sliding window
- Basic tree / graph traversal (BFS, DFS)
- Light dynamic programming (Fibonacci-class problems)

What is **rarely asked at graduate level**:
- Complex DP (LIS, edit distance variants)
- Advanced graph (Dijkstra, network flow)
- Segment trees, Fenwick trees
- Heavy bit manipulation puzzles

### Common question patterns by employer type

**Payments / Fintech (Stripe-like)**:
- Idempotency-aware design (e.g. "implement a function that processes refund
  requests safely under retries")
- Money-handling correctness (decimals, currency, rounding)
- API design with edge cases

**SaaS (Intercom / HubSpot / Squarespace style)**:
- Object-oriented design (e.g. "model a customer-support ticket system")
- Practical algorithm application (e.g. rate limiter, LRU cache)
- Database query thinking

**Infrastructure / Data (Datadog / MongoDB / Elastic)**:
- Performance-aware coding (Big-O reasoning expected)
- Concurrency primitives (locks, atomics — at least conceptually)
- Streaming / iterator patterns

## 3. Behavioural round patterns

Behavioural rounds at Dublin tech employers strongly emphasise:

- **Ownership** — "Tell me about a time you took responsibility for something outside
  your formal scope"
- **Conflict resolution** — "Describe a disagreement with a teammate and how you
  resolved it"
- **Learning velocity** — "Tell me about something complex you learned recently from
  scratch"
- **Failure recovery** — "Describe a project that didn't go as planned. What did you
  do?"

For graduates without industry experience, **academic projects, internships,
hackathons, open-source contributions, and significant student-society leadership
roles** are all acceptable source material for STAR-format answers.

## 4. System design at graduate level

Most Dublin employers do NOT expect full system design from new grads. When asked,
the bar is usually:

- Discuss high-level components (client, server, database)
- Identify what data needs to be stored and roughly how
- Recognise trade-offs between SQL and NoSQL at a basic level
- Spot obvious scalability concerns (single point of failure, hot path)

You are **not expected** to draw a full microservices architecture, choose specific
sharding strategies, or design a distributed consensus protocol.

## 5. Take-home assignments (when used)

Some employers prefer take-homes over live coding:
- Typical scope: 3-6 hours of work
- Common deliverable: small CRUD application or data-processing script with
  README explaining design decisions
- **What evaluators look for**: clean code, tests, README quality, sensible
  trade-offs explained — NOT cleverness or over-engineering

A common failure mode: candidates spend 15+ hours over-polishing. **Stop at the
stated time budget and document what you would do with more time.**

## 6. Red flags interviewers look for

Across Dublin employers, these are commonly cited as fast rejection signals at
graduate level:

- Inability to explain time/space complexity of one's own code
- Writing code without first clarifying requirements
- Refusing to discuss trade-offs ("there's no right answer" answered with silence)
- Visible panic or shutdown when stuck on a problem (vs asking for hints)
- For non-native English speakers: not asking for clarification when something is
  unclear (interviewers prefer questions to silent guessing)

## 7. What's typically out of scope for graduate interviews

- Production debugging of unfamiliar codebases
- Large-scale system design from scratch
- Detailed knowledge of a specific company's tech stack (high-level familiarity is
  enough)
- Algorithm research / novel approaches

---

*Source: aggregated from publicly observable interview practices and published
hiring guides of Dublin-based tech employers profiled in this knowledge base.
For company-specific details, see the individual company profile in
`01_companies/`.*
