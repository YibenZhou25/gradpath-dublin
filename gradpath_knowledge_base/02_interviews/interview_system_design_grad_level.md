# System Design at Graduate Level — Dublin Tech Interviews

> What system design rounds typically look like for graduate / junior software engineering
> roles in Dublin, calibrated to the actual bar set by Stripe, Intercom, Datadog,
> Pinterest, and similar mid-to-large tech employers.

## Will you face system design as a graduate?

The honest answer: **sometimes**. Distribution by employer type:

| Employer type | System design at grad level? |
|---------------|------------------------------|
| Big Tech (Microsoft, Google, Meta, Amazon, LinkedIn) | Often, but scaled-down |
| Mid-size SaaS (Stripe, Intercom, HubSpot, Datadog) | Sometimes, light version |
| Smaller / niche SaaS (Tines, Klaviyo, Squarespace) | Rarely at grad level |
| Consulting (Accenture, Avanade) | No, replaced by case study |

If you do face it as a grad, expect a **30-45 minute conversation**, not a 60-minute
deep-dive. The goal is to test that you can think structurally, not that you have
production system design experience.

## The 6-step framework that works for graduate-level questions

Use this as your default structure when the interviewer says "design a..."

### Step 1: Clarify requirements (5 minutes)

Ask:
- "What's the primary use case? Who are the users?"
- "What's the expected scale? Hundreds, millions, billions of requests?"
- "Should I focus on read-heavy or write-heavy patterns?"
- "Are there latency requirements I should optimise for?"
- "What features should I treat as in-scope vs out-of-scope?"

Failing to clarify is a fast rejection signal. Even if the interviewer hand-waves
the answers, they are watching whether you ask.

### Step 2: Functional and non-functional requirements (3 minutes)

State explicitly:
- Functional: what the system DOES (post a tweet, follow a user, render feed)
- Non-functional: how WELL it does it (availability targets, latency, consistency
  trade-offs)

This step is what separates "students who memorised system design" from "students
who think about systems".

### Step 3: High-level diagram (5-10 minutes)

Draw boxes for:
- Client (web, mobile, API consumer)
- Load balancer / API gateway
- Application servers
- Database(s)
- Cache layer if appropriate
- Async / message-queue layer if appropriate

Connect them with arrows showing data flow. **Talk while you draw** — the
interviewer evaluates your reasoning, not your drawing skill.

### Step 4: Data model (5 minutes)

For 1-3 key entities, sketch:
- The fields you'd store
- Primary key and any obvious indexes
- Relationships between entities

Choose SQL vs NoSQL with a stated reason. "I'd use Postgres because the
relationships between users and posts benefit from joins, and we don't yet need
horizontal scaling" is a strong answer. "I'd use MongoDB because it's web-scale"
is a fast rejection signal.

### Step 5: Identify bottlenecks and scale up (10 minutes)

Pick the path that bottlenecks first under load. Discuss:
- What does the database look like at 100x scale? Read replicas? Sharding?
- Where would caching help? What's the invalidation strategy?
- Could any expensive operation be made async via a queue?

You don't need to solve everything. **Naming the bottleneck and proposing a
direction is enough at graduate level.**

### Step 6: Address one trade-off in depth (5 minutes)

Pick one decision and articulate the trade-off. Examples:
- "I chose strong consistency for the payment write but eventual consistency for
  the feed generation, because..."
- "I'd use a write-through cache here at the cost of higher write latency,
  because read traffic dominates 100:1"

Showing you can reason about trade-offs is the single highest-value signal at
graduate-level system design.

## Five questions that recur across Dublin interviews

These are the patterns most often asked at graduate level — prepare a structured
approach for each:

1. **URL shortener** — bit.ly clone. Tests: hashing, database choice,
   read-heavy optimisation, custom-alias handling
2. **Social feed** — Twitter / Instagram simplified. Tests: fan-out vs fan-in
   trade-off, ranking, caching strategy
3. **Rate limiter** — limit requests per user. Tests: token bucket vs sliding
   window, distributed-state handling
4. **Notification system** — push notifications at scale. Tests: queue design,
   retry logic, idempotency
5. **Chat / messaging** — 1-on-1 messaging. Tests: real-time delivery, message
   ordering, offline-then-online sync

For each, write down a 5-minute mental rehearsal: clarifications, components,
data model, top bottleneck, one trade-off.

## What graduate-level system design is NOT testing

It is NOT testing whether you have:
- Built systems at the scale of Twitter or Stripe
- Memorised the internals of Cassandra or Kafka
- Designed for million-RPS workloads
- Implemented distributed consensus

If the interviewer pushes you into territory clearly above your experience level,
it is acceptable (and recommended) to say: "I don't have direct experience at
that scale, but my reasoning would be..." and then attempt the answer
analytically.

## Mental traps that hurt grad-level candidates

### Trap 1: Jumping to implementation too fast

Within 30 seconds of hearing the question, students often start drawing servers
and databases. **Slow down.** Steps 1-2 (clarify, requirements) are 30% of your
score.

### Trap 2: Trying to use every fancy technology

Mentioning Kubernetes, Kafka, Redis, Elasticsearch, GraphQL, and gRPC in one
answer is a red flag, not green. Use what the problem requires. Justify each
choice.

### Trap 3: Refusing to draw until you have the perfect plan

Drawing IS thinking in system design. Sketch, revise, re-sketch. Interviewers
expect iteration.

### Trap 4: Going silent when stuck

If you don't know something, say so and reason aloud about how you would figure
it out. Silent thinking reads as confusion. Out-loud reasoning reads as
problem-solving.

### Trap 5: Not asking the interviewer for guidance

If you've been on a topic for 10 minutes and aren't sure they're getting what
they want, ask: "Would you like me to go deeper here, or move on to another
area?" This signals professional collaboration, not weakness.

---

*Source: aggregated from publicly observable interview practices and published
system-design preparation resources, calibrated to graduate-level expectations
at Dublin tech employers profiled in this knowledge base.*
