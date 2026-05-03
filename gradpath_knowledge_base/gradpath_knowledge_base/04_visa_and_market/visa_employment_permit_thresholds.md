# Employment Permit Salary Thresholds · 2026 Reference

> Reference summary of the salary thresholds that determine employment-permit
> eligibility in Ireland, formatted for use by the assistant when computing visa
> feasibility for a specific job offer.
>
> **Last verified: April 2026.** Reflects thresholds that took effect on
> **1 March 2026** under the Department of Enterprise, Tourism and Employment
> (DETE) Roadmap for Minimum Annual Remuneration (MAR).
>
> Always verify current values at https://enterprise.gov.ie/ before relying on
> any specific figure for a real decision.

## Why salary thresholds matter

Employment-permit eligibility in Ireland is determined by:
1. The role itself (occupation classification under SOC 2010)
2. The offered salary, which must meet or exceed the applicable Minimum Annual
   Remuneration (MAR) threshold

Below threshold, even an otherwise-eligible role cannot generate a permit.
Above threshold, the role becomes eligible for the corresponding permit type
(subject to other criteria).

## Threshold reference (effective 1 March 2026)

The thresholds below took effect on 1 March 2026 under the new Roadmap
published by DETE on 2 December 2025. They represent a 7.66% increase from the
prior thresholds and are calculated based on a 39-hour working week.

### Critical Skills Employment Permit (CSEP) thresholds

| Sub-route | 2026 threshold | Notes |
|-----------|---------------|-------|
| Standard CSEP (with relevant degree, role on CSOL) | **€40,904** | Most graduate SWE/Data/ML roles |
| Recent Graduate CSEP (relevant degree, graduated within 12 months) | **€36,848** | Re-introduced from 1 March 2026 |
| CSEP without degree (relevant experience required) | **€68,911** | Used for senior/specialist non-degree paths |

### General Employment Permit (GEP) thresholds

| Sub-route | 2026 threshold | Notes |
|-----------|---------------|-------|
| Standard GEP | **€36,605** | Plus Labour Market Needs Test required |
| Recent Graduate GEP (Irish institution, graduated within 12 months) | **€34,009** | Re-introduced from 1 March 2026 |

### Other permit types (for reference)

| Permit type | 2026 threshold |
|-------------|---------------|
| Intra-Company Transfer Employment Permit | €49,523 |
| Healthcare assistants, home carers, meat processors, horticulture workers | €32,691 |
| Reactivation Employment Permit | National minimum wage (€14.15/hr in 2026) |

### Comparison: 2025 vs 2026

| Permit type | Pre-1-March-2026 | Post-1-March-2026 | Change |
|-------------|------------------|-------------------|--------|
| CSEP standard | €38,000 | €40,904 | +7.66% |
| CSEP without degree | €64,000 | €68,911 | +7.66% |
| GEP standard | €34,000 | €36,605 | +7.66% |
| Intra-Company Transfer | €46,000 | €49,523 | +7.66% |
| Sub-standard (healthcare, etc.) | €30,000 | €32,691 | +9.0% |

Future increases are scheduled annually through 2030, with indexation to
Central Statistics Office (CSO) wage data.

### Key implication for international CS graduates

For a typical multinational tech employer offer in Dublin (Stripe, Datadog,
Microsoft, Google, etc.), the offer comfortably exceeds even the highest
applicable threshold (€68,911 for the no-degree route). Salary is rarely the
binding constraint at this employer tier.

For offers from smaller Irish employers or banking-IT roles where graduate
salaries can sit in the €40,000-€50,000 range, the **Recent Graduate CSEP
threshold of €36,848** is highly relevant — it can be the difference between
qualifying and not qualifying within the 12-month-post-graduation window.

## Computational logic for visa feasibility

When the assistant is asked "does this offer qualify for visa sponsorship",
it should reason as follows:

```
Given: offered salary S (EUR base salary), role description R,
       graduation date G, application date A

Step 1: Identify role classification
   Is R likely to map to a Critical Skills List occupation?
   (Use visa_critical_skills_cs_roles.md as reference. ICT/SWE/Data/ML
    roles are almost always on the CSOL.)

Step 2: Determine recent-graduate eligibility
   IF (A - G) <= 12 months AND candidate has relevant degree:
       recent_graduate_route = AVAILABLE
   ELSE:
       recent_graduate_route = NOT_AVAILABLE

Step 3: Determine the relevant threshold
   IF role is on CSOL:
       IF recent_graduate_route AND degree-from-recognised-institution:
           threshold = 36848
           permit_type = "CSEP (Recent Graduate route)"
       ELSE:
           threshold = 40904
           permit_type = "CSEP (Standard route)"
   ELIF role requires a degree, NOT on CSOL but high salary:
       threshold = 68911
       permit_type = "CSEP (high-salary non-CSOL route)"
   ELSE:
       IF recent_graduate_route AND Irish-institution:
           threshold = 34009
           permit_type = "GEP (Recent Graduate route, with LMNT)"
       ELSE:
           threshold = 36605
           permit_type = "GEP (Standard route, with LMNT)"

Step 4: Compare
   IF S >= threshold:
       feasibility = "salary exceeds threshold by €" + (S - threshold)
   ELSE:
       feasibility = "salary below threshold by €" + (threshold - S)
                     + " — permit unlikely without salary adjustment"

Step 5: Factor employer willingness
   The above is necessary but not sufficient. The employer must also be
   willing to sponsor.

Step 6: Output
   Recommendation with all caveats. Recommend verification with employer HR.
```

## What the assistant should always include in feasibility output

When reporting visa feasibility for an offer, the assistant should always
include:

1. **The threshold being compared against**, including which sub-route applies
2. **Whether the user qualifies for the recent-graduate threshold** (this is
   the most-often-overlooked element under the new 2026 rules)
3. **The headroom or shortfall** with concrete EUR figure
4. **The permit type implied** with full name (CSEP / GEP)
5. **Caveats:**
   - Threshold values are 2026 — will increase annually through 2030
   - Employer willingness is a separate check
   - Final classification is determined by the employer's permit application
6. **Suggested next action** — usually: confirm sponsorship with employer's HR,
   and verify whether the role will be classified under CSOL

## Edge cases the assistant must handle

### Edge case 1: User on second year of Stamp 1G past the 12-month graduation window

If the user has already used their first year of Stamp 1G and graduation was
more than 12 months ago, the recent-graduate threshold (€36,848 / €34,009)
is **no longer available**. They default back to the standard threshold
(€40,904 / €36,605). This is a common trap and the assistant should flag it.

### Edge case 2: Salary stated as a range

JDs often state ranges like "€40,000–€50,000". The assistant should:
- Compute feasibility against both ends
- Note that under the standard CSEP threshold, the lower end of the range
  (€40,000) would actually fail by €904. The user should negotiate up or
  confirm the offer will be at least €40,904.
- Note the recent-graduate threshold flexibility if applicable.

### Edge case 3: Salary including bonus and stock

The threshold applies to **base salary**, not total compensation. Bonuses,
stock vests, and benefits do not count toward the MAR threshold. The assistant
should clarify this for users excited about high TC packages with relatively
low base.

### Edge case 4: Hybrid roles

Some roles combine technical and non-technical responsibilities. The employer's
permit application picks a single SOC code. The assistant should note the user
should ask HR which SOC code they intend to use, since this determines whether
CSEP or GEP applies.

### Edge case 5: User reports an offer below threshold

The assistant should NOT discourage negotiation. Many initial offers can be
adjusted. The assistant should:
- State the exact shortfall in EUR
- Suggest the user ask HR explicitly whether they can adjust to meet the
  threshold (employers familiar with permit processes know they need to)
- Note that a €904 shortfall on a CSEP offer is much easier to negotiate than
  a €5,000 shortfall

### Edge case 6: Salary in non-EUR currency

For roles offered in Ireland, payment is generally in EUR. If a candidate is
relocating from another currency zone and comparing offers, the threshold
applies to the EUR amount the candidate will actually receive in Irish payroll.

## Critical caveat

These thresholds change annually. The values in this file reflect the
post-1-March-2026 state. The assistant should treat them as current as of
April 2026 and recommend the user verify against the official source before
making decisions, particularly if the decision is several months in the future.

If the assistant is making a near-threshold determination (within €2,000 of
the threshold), it should explicitly recommend the user verify the current
threshold and confirm with employer HR before treating the result as actionable.

---

*Sources:*
- *Department of Enterprise, Tourism and Employment (enterprise.gov.ie)*
- *"Government unveils roadmap for gradual increase in employment permit salary
  thresholds", DETE press release, 2 December 2025*
- *Employment Permits Minimum Annual Remuneration: Outcome of the Roadmap
  Review 2025 (official PDF)*
- *Last verified: April 2026.*
