# Before / After — How iteration changed Claude's behavior

Sources: `outputs/baseline-review.md` (**Before** — no methodology),
`outputs/readiness-review.md` (**After** — with methodology),
`skills/enterprise-readiness/SKILL.md` (what changed between them).
Quoted passages are taken verbatim from those files. `…` marks where a passage is
shortened; nested quotation marks and trailing punctuation at a trim point are
adjusted. Nothing below is paraphrased.

---

## 1. Certainty → calibrated uncertainty

**Before** — baseline GlobalBank conclusion:

> "## GlobalBank — Sep 30 launch is not achievable"
> "Sep 30 has no viable path. Realistic earliest production is late October at the soonest, more likely November, and only if the Oct 15 date holds."

**What I observed.** The baseline jumped from a real dependency problem to a closed verdict, and attached delivery windows ("late October … more likely November") the source data does not support.

**What I changed in the methodology.**
- Principle 11: "Do not invent decision dates, delivery windows, review durations, effort estimates, financial exposure, or deadlines when the source information does not support them."
- Principle 12: "Before writing 'will fail' or 'cannot be achieved,' test whether any of the following could change the outcome" — an interim control, a scope change, an acceleration, an alternative path. "If such a path exists and has not been evaluated, classify the outcome as **at risk** and name the specific question that must be resolved …"

**After** — final GlobalBank conclusion:

> "## E1 — GlobalBank: the September 30 launch date will not be met on the current plan"
> "The date cannot be met if the automated-provisioning requirement stands as written. Two paths could in principle still preserve it, and **neither has been evaluated**: (a) the customer agrees to waive automated provisioning as a production gate for launch; (b) Security accepts an interim compensating control for provisioning/deprovisioning, and Compliance and the customer then approve within the window. Absent a decision on one of those, the date does not hold."
> "The revised-date decision cannot be computed from available information — it depends on the October 15 target holding plus Security, Compliance, and customer-approval durations that no source provides."

**Why it matters for a horizontal TPM.** A horizontal TPM has to be believed across functions. "Impossible" ends the conversation; "not achievable on the current plan unless (a) or (b) proves viable" keeps the two live options visible and still forces a decision — without inventing dates the TPM would later be held to.

---

## 2. Status → decision support

**Before** — how the baseline handled Northstar / RBAC:

> "Engineering has done early exploration only, with **no delivery date because it has not been prioritized**."
> "Without a prioritization decision this month, Nov 15 will slip."
> "**RBAC prioritization.** Decide whether granular / separated admin roles enters the committed roadmap. Two active enterprise deals ($ + Q4 expansion) depend on it; today it has no date."

**What I observed.** The problem was correctly surfaced, but left as a flag: no accountable owner, no stated missing input, and a timeframe ("this month") the data does not support.

**What I changed in the methodology.**
- Principle 3: "A risk that does not point to a decision is just commentary" — every material risk must carry a decision required, a **decision owner**, the dependency chain, information still needed, and the consequence of no decision.
- Principle 4: "Explicitly identify missing information".
- Principles 8 and 10: "Do not make another function's decision for it"; "Keep human accountability explicit".

**After** — the final review (`readiness-review.md`, item E2) routes the same signal to a decision:

> "**Decision required.** Prioritize granular RBAC and customer-facing audit export for Northstar — each with a committed date and allocated capacity — **or** decide now to re-baseline November 15 and tell the customer. This requires an engineering effort estimate for both capabilities as its first input."
> "**Who owns it.** Product (roadmap prioritization) and Engineering (effort, date, capacity) leadership. Sales / executive sponsor if the date moves. TPM frames the trade-off and supplies the dependency picture; TPM does not set priority and does not pre-judge whether Security or Compliance will approve."
> "**If we do nothing.** November 15 slips."

**Why it matters for a horizontal TPM.** The TPM has no authority over Product, Engineering, or Security. The leverage is converting a cross-functional signal into one decision that a named owner can act on, plus the single input that unblocks it — not adding another red status to a tracker.

---

## 3. Customer issues → portfolio reasoning

**Before** — the baseline already connected the two accounts:

> "Admin-role separation is a form of the same granular RBAC capability that is unprioritized and undated for Northstar."
> "This is the single highest-leverage prioritization decision in the portfolio."

**What I observed.** The shared-capability link was made — but the baseline moved straight to advocacy ("single highest-leverage prioritization decision") without weighing whether building it was the right call: no look at reuse, effort, alternatives, or capacity.

**What I changed in the methodology.**
- Principle 5: "Map each customer requirement to the underlying capability, then group by capability. A gap that blocks one customer is a risk; a gap that blocks several is a portfolio problem and a prioritization question."
- Principle 6: "Multiple requests raise the question; they do not answer it" — weigh strategic reuse, urgency, customer impact, regulatory / security exposure, effort, alternatives, and available capacity; "the prioritization decision itself belongs to the accountable owners."

**After** — the final version names the shared capability and stops short of recommending the build:

> "| Northstar Health | 'granular administrator permissions' | Granular RBAC |"
> "| Mercury Retail | 'separation between administrator roles' | Granular RBAC (admin-role subset) |"
> "Multiple customer requests raise the question of building it; they do not settle it — the decision needs a deliberate weighing of strategic reuse, urgency, customer impact, regulatory exposure, engineering effort, alternatives, and available capacity …"
> "This review does **not** recommend building it on the strength of two requests; it recommends the decision be made deliberately with those inputs."

The supporting seven-factor evaluation records what is still unknown — "**Effort — UNKNOWN**", "**Available capacity — NONE ALLOCATED**" — and asks Engineering for "a scoped-down admin-role-separation option" as an input.

**Why it matters for a horizontal TPM.** Seeing that two escalations are one capability decision is the horizontal TPM's core value. Deciding to build it is not the TPM's call — so the output frames the trade-off and hands it to Product and Engineering, rather than pre-committing the roadmap.
