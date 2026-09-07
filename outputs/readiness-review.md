# Enterprise Readiness Review — Week of September 6, 2026

> **Final output — produced _with_ [`../skills/enterprise-readiness/SKILL.md`](../skills/enterprise-readiness/SKILL.md) applied.**
> Compare with the pre-methodology [`baseline-review.md`](./baseline-review.md); the differences
> are analyzed in [`../assets/before-after.md`](../assets/before-after.md).

Prepared by: TPM, Enterprise Readiness
Method: applies `skills/enterprise-readiness/SKILL.md` (principles 1–15)

**How to read this document.** The **Executive Review** below is the primary output:
for each item it answers what needs attention, why it matters, the decision required,
who owns it, and what happens if we do nothing. Everything after the divider —
evidence and citations, assumptions, full dependency analysis, the cross-customer
capability evaluation, and what we don't yet know — is **supporting analysis**.

Dates are used only where a source provides them (customer targets, the provisioning
target) or where they follow by arithmetic from today (2026-09-06). Where timing
matters but no source supports a specific date, this review says so and names who
must provide it, rather than inventing one.

---

# Executive Review

## E1 — GlobalBank: the September 30 launch date will not be met on the current plan

**What needs attention.** GlobalBank ($8M ACV) has a September 30 production target — 24
days out. It requires automated user provisioning for production; provisioning is not yet
generally available and its earliest engineering target is October 15 (engineering
confidence: medium). Security's access-control review cannot complete until provisioning
can be demonstrated, and Compliance's production approval depends entirely on that review.
Separately, Sales reports the date is still committed externally, the customer has **not**
been told of any risk, and the account team reports strong customer confidence.

**Why it matters.** The earliest prerequisite lands after the committed date, with two
further sequential approvals (Security, then Compliance, then the customer's own security
approval) downstream of it. The customer is the only party not operating on the revised
timeline, on the largest account in the portfolio. Contract terms tied to the launch date
are not known to this review and could raise the stakes further.

**Is it truly impossible?** The date cannot be met if the automated-provisioning
requirement stands as written. Two paths could in principle still preserve it, and
**neither has been evaluated**: (a) the customer agrees to waive automated provisioning as
a production gate for launch; (b) Security accepts an interim compensating control for
provisioning/deprovisioning, and Compliance and the customer then approve within the
window. Absent a decision on one of those, the date does not hold.

**Decision required.**
1. Set a defensible internal GlobalBank production date, or decide to pursue path (a) or
   (b) above.
2. Decide what GlobalBank is told about the revised timeline and current risk, and when.
3. Sub-question for Security: is an interim compensating control for manual deprovisioning
   needed for GlobalBank in the meantime? (Security's own general guidance flags manual
   deprovisioning as possibly insufficient for large regulated enterprises.)

**Who owns it.** Revised date — Product + Engineering leadership. Paths (a)/(b) and the
customer conversation — Sales / account leadership with executive-sponsor sign-off.
Interim control sufficiency — Security. TPM coordinates; TPM sets none of these.

**If we do nothing.** GlobalBank learns of the slip at or near September 30 with no
warning: reference and trust damage on an $8M account, possible contractual exposure, and
loss of Sales credibility on future commitments.

**Timing.** The customer-communication decision is urgent now: the committed date is 24
days away and the customer is uninformed. The revised-date decision cannot be computed
from available information — it depends on the October 15 target holding plus Security,
Compliance, and customer-approval durations that no source provides.

---

## E2 — Northstar Health: the November 15 target is at risk; two required capabilities are uncommitted

**What needs attention.** Northstar (regulated healthcare) targets November 15 — about ten
weeks out — and treats granular administrator permissions and customer-accessible audit
history as firm enterprise requirements. Today the product has only Admin/User roles and
no customer log export. Granular RBAC has had early engineering exploration only, with no
delivery date because it is not prioritized. Customer-facing audit export is undated
additional engineering work. Security expects customer-facing audit evidence to be
required before it approves production. Compliance's regulatory assessment is open and
waiting on the customer's security questionnaire, which is still in progress.

**Why it matters.** The date depends on two capabilities that currently have no owner, no
committed date, and no allocated capacity, plus an approval chain that has not begun to
clear. The runway is about ten weeks against work that is not yet scheduled; slack is
minimal.

**Is it truly impossible?** No — a path exists if granular RBAC and audit export are
prioritized now with committed dates and capacity, and the questionnaire is completed
promptly. Whether that path is real depends on the engineering effort estimate for each
capability, which does not exist yet. Until it does, this is **at risk**, not failed.

**Decision required.** Prioritize granular RBAC and customer-facing audit export for
Northstar — each with a committed date and allocated capacity — **or** decide now to
re-baseline November 15 and tell the customer. This requires an engineering effort
estimate for both capabilities as its first input.

**Who owns it.** Product (roadmap prioritization) and Engineering (effort, date, capacity)
leadership. Sales / executive sponsor if the date moves. TPM frames the trade-off and
supplies the dependency picture; TPM does not set priority and does not pre-judge whether
Security or Compliance will approve.

**If we do nothing.** November 15 slips. Because the customer treats these as hard
requirements in a regulated environment, exposure extends to the deal and renewal, not
just the date. The Compliance assessment stays blocked. The slip is discovered late — the
same pattern as GlobalBank (see E5).

**Timing.** This-week-urgent, on the reasoning above (ten-week runway, unscheduled work,
regulated reviews still to run). A precise drop-dead date cannot be derived from available
information and must come from the engineering estimate.

---

## E3 — Mercury Retail: Q4 expansion is at risk; admin-role separation has no date

**What needs attention.** Mercury plans a Q4 expansion across 14 European markets and
requires separation between administrator roles. The product has a single Admin role;
admin-role separation is a form of the same granular RBAC capability that is uncommitted
and undated (see E4). The account team reports the expansion is on plan, and the customer
has already asked when granular administrator permissions will be available. The EU
data-governance review, which must complete before expansion, has begun with no material
findings yet — the one part of this that is moving.

**Why it matters.** "On plan" rests on a capability with no delivery date, and the
customer is already tracking that date as a gating item. The compliance track is
progressing; the product/engineering track is not.

**Is it truly impossible?** No, and it has more runway than Northstar. A path exists if
admin-role separation is prioritized — and it may be a smaller, separable change than full
RBAC, which would improve the odds. Whether that is true is an open question for
Engineering.

**Decision required.**
1. Confirm whether admin-role separation is in scope of the granular RBAC decision (E4) or
   can be delivered as a scoped-down standalone change, and on what timeline.
2. Decide what date the account team gives the customer.

**Who owns it.** Product + Engineering leadership (same forum as E4). TPM consolidates;
TPM commits no date.

**If we do nothing.** The account team keeps reporting "on plan" on a basis that is not
supported; the customer asks again; the expansion slips past Q4; EU data-governance effort
risks running ahead of a delivery that is not scheduled.

**Timing.** Less acute than Northstar — the target is end of Q4, and the specific date and
whether the 14-market rollout is phased are not given. But the decision is needed before
the account team gives the customer a date.

---

## E4 — Portfolio: granular RBAC is a shared platform gap and needs one prioritization decision

**What needs attention.** Two customers depend on the same missing capability, described in
different words:

| Customer | Stated requirement | Underlying capability |
|---|---|---|
| Northstar Health | "granular administrator permissions" | Granular RBAC |
| Mercury Retail | "separation between administrator roles" | Granular RBAC (admin-role subset) |
| GlobalBank | access-control review expectations | Adjacent (same domain, not a direct ask) |

It has had early exploration only and is not on the roadmap. Treating it as two separate
account escalations will produce two separate partial answers.

**Why it matters.** This is one prioritization decision that affects at least two
enterprise commitments, one of them regulated. Multiple customer requests raise the
question of building it; they do not settle it — the decision needs a deliberate weighing
of strategic reuse, urgency, customer impact, regulatory exposure, engineering effort,
alternatives, and available capacity (full evaluation in supporting analysis S3).

**Decision required.** Product + Engineering leadership to take granular RBAC as a single
portfolio decision, with (a) an engineering delivery estimate and (b) a scoped-down
admin-role-separation-only option requested as inputs. This review does **not** recommend
building it on the strength of two requests; it recommends the decision be made
deliberately with those inputs.

**Who owns it.** Product + Engineering leadership. TPM prepares the trade-off brief.

**If we do nothing.** Northstar and Mercury both drift with no owner; the capability keeps
getting deferred because no single account decision is large enough to force it; the
company re-learns the same gap on the next enterprise deal.

**Timing.** Tied to E2 — the same this-week prioritization forum.

---

## E5 — Systemic: external commitments are ahead of internal readiness on all three accounts

**What needs attention.**

| Account | External position | Internal reality |
|---|---|---|
| GlobalBank | Sep 30 committed; "strong customer confidence"; customer not told of risk | Provisioning targeted Oct 15 (medium); Security review not started; Compliance gated |
| Northstar | Nov 15 is the customer's expectation; requirements treated as firm | Two capabilities unprioritized and undated; questionnaire incomplete |
| Mercury | "On plan per account team" | Required capability has no date; customer already asking |

This is three of three accounts.

**Why it matters.** Account teams are reporting confidence against original commitments
while Engineering, Security, and Compliance work to the real constraints. The reconciliation
is currently happening only in this review. That makes it a process problem, not just three
separate risks — and it will recur on the next cohort of enterprise deals.

**Decision required.**
1. Per-account reconciliation — covered by E1, E2, E3.
2. A process norm: customer-facing launch-date confidence is not reported without a joint
   readiness sign-off across Product, Engineering, Security, and Compliance.

**Who owns it.** Process norm — Sales leadership plus Product/Engineering leadership, with
executive sponsorship. TPM would operate the sign-off; TPM does not own Sales
communications.

**If we do nothing.** Late discovery of slippage becomes the default failure mode for
enterprise launches.

**Timing.** Per-account items are urgent now; the process norm is not date-bound but should
be settled while these three cases make the cost concrete.

---

## E6 — Systemic: no engineering capacity is allocated, and E1, E2, E4 compete for it

**What needs attention.** Engineering reports no additional capacity is currently
allocated. GlobalBank provisioning (committed, no buffer), granular RBAC (two customers),
and customer-facing audit export (one customer plus a Security precondition) all draw on
the same unallocated capacity.

**Why it matters.** They cannot all be accelerated. Today's implicit outcome is that
provisioning gets attention and RBAC and audit export get nothing — a prioritization
decision that is being made by default rather than deliberately.

**Decision required.** Add capacity, or consciously sequence the work (for example
provisioning, then admin-role separation / RBAC, then audit export) with customer dates and
communications aligned to that sequence.

**Who owns it.** Engineering leadership plus executive (headcount/budget); Product for
sequencing.

**If we do nothing.** Prioritization continues to happen by escalation volume; Northstar
and Mercury keep drifting.

**Timing.** This is an input to the E2/E4 prioritization decision and shares its urgency.

---

## What this review does not know

Five gaps could each move the assessment materially. Full detail in supporting analysis S5.

- **Engineering effort estimates** for granular RBAC and for customer-facing audit export.
  These determine whether Northstar's November 15 and Mercury's Q4 are recoverable at all.
- **Security and Compliance review durations** for GlobalBank once provisioning is
  demonstrable. These determine any realistic revised GlobalBank date.
- **What "medium confidence" on October 15 means** in potential weeks of slip.
- **GlobalBank contract terms** on the launch date (penalties, termination rights, or a
  soft target). This changes how urgent and how senior the customer conversation is.
- **Legal and Support readiness** — absent from all source inputs, though both are in the
  TPM's remit. Mercury's EU expansion likely has a Legal/DPA component; three enterprise
  launches in one quarter is an unassessed Support load.

---
---

# Supporting Analysis

Not for the executive view. Evidence tags: **FACT** (stated in a source), **INFERENCE**
(derived by connecting facts), **ASSUMPTION** (believed, not established; load-bearing
noted), **RECOMMENDATION** (proposed action, not a decision and not made on any function's
behalf).

## S1 — Evidence base

### GlobalBank
- **FACT** (customers.md): target production launch September 30; ACV $8M; operates US/UK/EU;
  SSO and automated user provisioning mandatory for production; customer security approval
  required before production access.
- **FACT** (product.md): SSO generally available; automated user provisioning planned, not
  yet GA.
- **FACT** (engineering.md): SSO production implementation complete; automated provisioning
  target moved from September 15 to October 15; engineering confidence medium; no
  additional engineering capacity allocated.
- **FACT** (security.md): access-control review open; cannot complete until automated
  provisioning controls can be demonstrated; general note that manual user deprovisioning
  may not meet access-control expectations for larger regulated enterprises.
- **FACT** (compliance.md): no outstanding general compliance findings; production approval
  depends on completion of Security's access-control review.
- **FACT** (sales.md): September 30 committed externally; customer not informed of launch
  risk; account team reports strong customer confidence.
- **INFERENCE**: September 30 cannot be met on the current plan — earliest provisioning
  (October 15) is after the launch date, and Security review, Compliance approval, and
  customer approval are sequential and downstream of provisioning.
- **ASSUMPTION** (high load for any revised date; low load for the September 30 conclusion):
  October 15 is best-case given medium confidence and no buffer; slip beyond it is
  plausible.
- **ASSUMPTION** (medium load): "automated user provisioning" includes automated
  deprovisioning. If not, the manual-deprovisioning control gap persists past October 15.
- **ASSUMPTION** (untested, would preserve September 30 if true): the customer would not
  waive automated provisioning as a production gate, and Security would not accept an
  interim compensating control. Neither has been asked.

### Northstar Health
- **FACT** (customers.md): target November 15; requires granular administrator permissions
  and customer-accessible audit history; security questionnaire in progress; regulated
  healthcare environment.
- **FACT** (product.md): two roles only (Admin, User); granular RBAC under consideration,
  not committed to roadmap; customers cannot export their own audit logs.
- **FACT** (engineering.md): early technical exploration for granular RBAC complete; no
  delivery date because not prioritized; customer-facing audit export would require
  additional engineering work.
- **FACT** (security.md): expects customer-facing audit evidence to be required before
  production approval.
- **FACT** (compliance.md): regulatory assessment open pending completion of the security
  questionnaire.
- **FACT** (sales.md): November 15 remains the customer expectation; customer views
  auditability and administrator controls as enterprise requirements.
- **INFERENCE**: November 15 (~10 weeks from 2026-09-06) depends on two capabilities with
  no committed date, no allocated capacity, and an approval chain that has not begun to
  clear.
- **ASSUMPTION** (high load): "granular administrator permissions" = "granular RBAC" in
  product/engineering terms; "customer-accessible audit history" = the customer-facing
  audit export Engineering describes.
- **ASSUMPTION** (high load): no engineering capacity is available without displacing
  committed work (engineering.md states none allocated; RBAC and audit export are "not
  prioritized").

### Mercury Retail
- **FACT** (customers.md): expansion across 14 European markets planned for Q4; requires
  separation between administrator roles; EU data-governance review must complete before
  expansion.
- **FACT** (product.md / engineering.md): single Admin role; granular RBAC uncommitted and
  undated.
- **FACT** (compliance.md): initial EU data-governance assessment has begun; no material
  findings yet.
- **FACT** (sales.md): account team reports Q4 expansion on plan; customer has asked when
  more granular administrator permissions will be available.
- **INFERENCE**: "separation between administrator roles" is a subset of granular RBAC —
  the same uncommitted capability affecting Northstar. The account team's "on plan" status
  depends on a capability with no date.
- **ASSUMPTION** (medium load): admin-role separation may be a smaller, separable change
  than full granular RBAC — relevant to the alternatives factor in S3.
- **ASSUMPTION** (medium load): "Q4" runs to approximately end of December; the specific
  deadline and any phasing are not stated.

## S2 — Full decision structure for each material risk

### R1 — GlobalBank September 30 date
- **What is happening**: provisioning target moved to October 15; Security review gated on
  it; Compliance gated on Security; customer uninformed; date still externally committed.
- **Why it matters**: $8M account, 24 days to a date that the dependency chain does not
  support; customer is the only party unaware.
- **Dependency chain**: automated provisioning GA (Oct 15, medium, no buffer) → Security
  access-control review → Compliance production approval → customer security approval →
  production access. Every link after provisioning starts after October 15.
- **Customers / capabilities affected**: GlobalBank directly; automated de/provisioning;
  access-control review process. Read-across to Northstar via the regulated-enterprise
  deprovisioning concern (R2, S3).
- **Decision required**: set a revised internal date, or pursue a scope waiver / interim
  control; decide customer communication.
- **Decision owner**: Product + Engineering (date); Sales + executive sponsor (customer,
  scope waiver); Security (interim control sufficiency).
- **Recommended next action**: **RECOMMENDATION** — TPM convenes a GlobalBank readiness
  sync this week (Engineering, Security, Compliance, Sales) to agree the internal position
  and the risk message; Sales then owns delivery to the customer.
- **When the decision is needed**: customer communication — now (24 days out, customer
  uninformed; both facts). Revised date — cannot be specified from available information;
  must be set by the functions above once review durations are known.
- **Consequence of no decision**: unwarned slip at/after September 30; trust, reference,
  and possible contractual damage on the largest account; Sales credibility.

### R2 — Manual deprovisioning may not satisfy GlobalBank's control expectations
- **What is happening**: **FACT** (security.md) manual deprovisioning flagged as possibly
  insufficient for large regulated enterprises; GlobalBank is a bank across US/UK/EU.
- **Why it matters**: a substantive control-gap risk, not only schedule — Security's review
  could raise findings even after provisioning ships if the interim story is weak.
- **Dependency chain**: manual deprovisioning in place until provisioning GA → Security
  review evaluates it → possible findings → remediation before approval.
- **Customers / capabilities affected**: GlobalBank (direct); Northstar (potential, also
  regulated, has not raised provisioning); automated de/provisioning.
- **Decision required**: whether an interim compensating control is needed pending
  automation.
- **Decision owner**: Security. TPM surfaces; TPM does not judge control adequacy.
- **Recommended next action**: **RECOMMENDATION** — TPM asks Security this week whether an
  interim control is required and confirms with Engineering that provisioning scope covers
  deprovisioning.
- **When the decision is needed**: as an input to R1's chain.
- **Consequence of no decision**: Security review stalls late or reopens after October 15,
  extending the GlobalBank timeline further.

### R3 — Northstar Health November 15: two uncommitted capabilities
- **What is happening**: granular RBAC and customer-facing audit export both required,
  both undated and unprioritized; security questionnaire incomplete; Compliance assessment
  blocked on it; Security expects audit evidence before approval.
- **Why it matters**: ~10-week runway against unscheduled work for a regulated customer
  that treats these as firm requirements.
- **Dependency chain**: (1) RBAC prioritized → dated → delivered → requirement met;
  (2) audit export prioritized → dated → delivered → requirement met and Security
  precondition met; (3) questionnaire completed → Compliance assessment proceeds →
  regulatory approval. Parallel; none currently moving toward November 15.
- **Customers / capabilities affected**: Northstar (direct); granular RBAC (shared, S3);
  customer-facing audit export (shared candidate, S3). Read-across to Mercury on RBAC.
- **Decision required**: prioritize both capabilities with dates and capacity, or
  re-baseline November 15.
- **Decision owner**: Product + Engineering leadership; Sales / executive sponsor if the
  date moves.
- **Recommended next action**: **RECOMMENDATION** — TPM prepares a one-page prioritization
  brief (deal context, dependency math, S3 seven-factor analysis, the capacity conflict
  with GlobalBank) for this week's Product/Engineering prioritization forum.
- **When the decision is needed**: this-week-urgent on the reasoning above; a precise
  deadline requires the engineering effort estimate.
- **Consequence of no decision**: November 15 slips; deal and renewal exposure given the
  regulated context; Compliance assessment stays blocked; late discovery.

### R4 — Mercury Retail Q4: admin-role separation undated
- **What is happening**: admin-role separation required; product has one Admin role;
  capability uncommitted and undated; customer already asking for a date; EU
  data-governance assessment underway with no findings yet.
- **Why it matters**: "on plan" rests on an undated capability; customer is tracking the
  date as gating.
- **Dependency chain**: admin-role separation prioritized → dated → delivered →
  requirement met. In parallel: EU data-governance assessment completed → expansion
  cleared. Compliance link progressing; capability link not.
- **Customers / capabilities affected**: Mercury (direct); granular RBAC / admin-role
  separation (shared, S3). Read-across to Northstar.
- **Decision required**: confirm whether admin-role separation is in scope of the RBAC
  decision or a scoped-down standalone change; decide the date given to the customer.
- **Decision owner**: Product + Engineering leadership (same forum as R3).
- **Recommended next action**: **RECOMMENDATION** — fold Mercury into the R3 / S3
  prioritization brief; ask Engineering whether admin-role separation is separable from
  full RBAC and cheaper to ship.
- **When the decision is needed**: before the account team gives the customer a date; less
  acute than Northstar (Q4 end vs November 15; exact date and phasing not given).
- **Consequence of no decision**: account team continues reporting "on plan" without
  support; customer asks again; expansion slips past Q4; EU data-governance effort may run
  ahead of an unscheduled delivery.

## S3 — Horizontal capability analysis

### P1 — Granular RBAC / admin-role separation: shared platform gap

Requirement-to-capability mapping is in E4. Two direct customer dependencies plus one
adjacent (GlobalBank), all on a capability with early exploration only and no roadmap
slot.

**Seven-factor evaluation** (Principle 6 — multiple requests raise the build question,
they do not answer it):

- **Strategic reuse — HIGH.** Granular admin roles / role separation is broadly expected
  across the enterprise segment, not specific to these accounts.
- **Urgency — HIGH (Northstar, ~10 weeks), MEDIUM-HIGH (Mercury, Q4).** Both undated today.
- **Customer impact — HIGH.** Northstar: firm requirement, regulated, renewal exposure.
  Mercury: 14-market expansion value, active unanswered customer question.
- **Regulatory / security exposure — MEDIUM-HIGH.** Northstar is regulated healthcare and
  frames this as compliance-grade, lifting it above preference.
- **Effort — UNKNOWN.** Only early exploration is complete; no delivery estimate exists.
  This is the single most important missing input (S5).
- **Alternatives — PARTIALLY OPEN.** A scoped admin-role-separation-only change may serve
  Mercury without full RBAC. Interim mitigations for Northstar's admin-permission needs are
  unclear. Audit export (P2) is a separate need, not an alternative.
- **Available capacity — NONE ALLOCATED.** Direct conflict with GlobalBank provisioning
  (committed, no buffer). Prioritizing RBAC without adding capacity displaces committed
  work; the trade-off must be named, not absorbed silently (E6).

**RECOMMENDATION.** Take granular RBAC to the prioritization forum this week as one
portfolio decision, with an engineering delivery estimate and a scoped-down
admin-role-separation option requested as inputs. Do not pre-commit to building it on the
strength of two requests. The decision belongs to Product + Engineering leadership.

### P2 — Customer-facing audit export: second, smaller shared gap

**FACT**: internal activity logging is stable (engineering.md); customers cannot export
their own logs (product.md). Required explicitly by Northstar and treated by Security as an
approval precondition for Northstar. Currently a **single-customer** requirement in the
data, so **not yet** a portfolio pattern — but it is the same shape as P1 (capability
exists internally; enterprise-grade customer-facing surface does not). **RECOMMENDATION**:
track whether any other enterprise/regulated account needs this; a second instance
promotes it to a P1-style portfolio decision.

## S4 — Commitments vs. readiness (detail for E5)

| Account | External commitment / signal | Source | Internal readiness | Source |
|---|---|---|---|---|
| GlobalBank | Sep 30 committed externally; customer not informed of risk; strong customer confidence | sales.md | Provisioning target Oct 15, medium confidence; Security review open and gated; Compliance gated on Security | engineering.md, security.md, compliance.md |
| Northstar | Nov 15 is the customer expectation; auditability and admin controls treated as enterprise requirements | sales.md, customers.md | Granular RBAC and audit export unprioritized and undated; questionnaire in progress; regulatory assessment blocked | product.md, engineering.md, compliance.md |
| Mercury | Q4 expansion "on plan" per account team | sales.md | Required admin-role separation uncommitted and undated | product.md, engineering.md |

**INFERENCE**: the reconciliation between these two columns is currently happening only in
this review. Three of three accounts show the pattern, which makes it a process finding
(E5), not only three individual risks.

## S5 — Missing information

| # | Unknown | What this review assumes without it | How the assessment moves if resolved |
|---|---|---|---|
| 1 | Engineering effort estimate for granular RBAC (and whether admin-role separation is separable) | Treated as multi-week, undated | A small scoped change could make Mercury Q4 and possibly Northstar Nov 15 viable; a large one confirms both slip |
| 2 | Engineering effort estimate for customer-facing audit export | Treated as undated additional work | Directly determines whether Northstar Nov 15 is recoverable |
| 3 | Security review duration for GlobalBank once provisioning is demonstrable | Not estimated | Determines any realistic revised GlobalBank date |
| 4 | Compliance approval duration for GlobalBank after Security completes | Not estimated | Same |
| 5 | What "medium confidence" on Oct 15 means in weeks of potential slip | Oct 15 treated as best-case, slip plausible | A firm Oct 15 tightens the GlobalBank re-baseline; a soft one widens it |
| 6 | Northstar security questionnaire completion status and blocker ownership | Assumed weeks from done | If near done, Compliance assessment can start soon and Nov 15 pressure eases slightly |
| 7 | GlobalBank contract terms on the launch date (penalties, termination rights, soft target) | Assumed material but not catastrophic | Penalty/termination clauses make E1's customer conversation urgent and executive-level immediately |
| 8 | Whether "automated provisioning" scope includes automated deprovisioning | Assumed yes | If no, R2's control gap persists past Oct 15 and needs its own remediation |
| 9 | Mercury's precise Q4 deadline and whether the 14-market rollout is phased | Assumed single ~end-of-December cutover | Phasing could let early markets launch on current capability while later ones wait |
| 10 | Whether any customer other than Northstar needs customer-facing audit export | Assumed single-customer | A second customer promotes P2 to a portfolio prioritization decision |
| 11 | Legal and Support readiness — absent from all source inputs | Assumed not yet assessed | Mercury EU expansion likely has a Legal/DPA component; three enterprise launches in one quarter is an unassessed Support load; either could surface new gating items |

## S6 — Watch list (does not yet pass the executive signal test)

- Customer-facing audit export as a platform pattern — single customer today (P2).
- Legal readiness for Mercury's EU expansion (DPA / data-governance legal component) — not
  in source inputs.
- Support readiness for three enterprise launches in one quarter — not in source inputs.
- Northstar automated provisioning — not raised by the customer yet, but Security's general
  concern about manual deprovisioning in regulated environments would apply.
- Mercury EU data-governance assessment — currently clean; confirm it stays clean as scope
  covers all 14 markets.

## Human accountability

This review is decision support for the TPM. It does not set roadmap priority, commit
engineering dates, judge the sufficiency of a security control, grant regulatory or
compliance approval, or decide what a customer is told. Each of those remains with the
named function and its accountable leader. Recommendations here are proposals to accept,
modify, or reject.
