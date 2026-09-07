# Enterprise Readiness Review — Week of September 6

> **Baseline output — produced _before_ the enterprise-readiness methodology existed.**
> Kept for comparison with the post-methodology [`readiness-review.md`](./readiness-review.md);
> the differences are analyzed in [`../assets/before-after.md`](../assets/before-after.md).

Prepared by: TPM, Enterprise Readiness
Sources: data/customers.md, product.md, engineering.md, security.md, compliance.md, sales.md

---

## Bottom line

| Customer | Target | Readiness verdict | Primary blocker |
|---|---|---|---|
| GlobalBank | Sep 30 | **Not achievable on date** | Automated provisioning (Oct 15 best case) gates the security review that gates production approval |
| Northstar Health | Nov 15 | **At serious risk** | Two required capabilities (granular admin permissions, customer audit export) are unprioritized with no engineering date |
| Mercury Retail | Q4 expansion | **At risk** | Admin role separation depends on the same uncommitted RBAC capability blocking Northstar |

All three customers are blocked, in whole or in part, by the **same two capability gaps**: automated provisioning and granular / separated admin roles. This is a portfolio problem, not three independent account problems.

---

## GlobalBank — Sep 30 launch is not achievable

**The commitment.** Sales reports Sep 30 as externally committed, the customer has not been told of any risk, and the account team reports strong customer confidence. Contract value is $8M.

**The dependency chain that breaks it:**

1. The customer requires SSO **and** automated user provisioning for production. SSO is done (Product GA, Engineering complete). Automated provisioning is **not** GA.
2. Engineering's provisioning date has already moved from Sep 15 to **Oct 15**, at *medium* confidence, with **no additional capacity allocated** — so there is no buffer and no accelerant.
3. Security cannot complete its access-control review **until automated provisioning controls can be demonstrated** — i.e. the review effectively cannot begin until after Oct 15.
4. Compliance production approval is explicitly **dependent on Security's review** completing. Compliance has no other outstanding findings, so Security is the whole gate.
5. The customer requires its own security approval before production access, which comes after our internal approval chain clears.

Even in the best case (provisioning lands exactly on Oct 15 and holds), Security review → Compliance approval → customer security approval all occur *after* Oct 15. Sep 30 has no viable path. Realistic earliest production is late October at the soonest, more likely November, and only if the Oct 15 date holds.

**The cross-functional gap no single function is reporting:** Sales confidence and the external Sep 30 commitment are still based on the original timeline. Engineering, Security, and Compliance are all already operating on the slipped one. The customer is the only party who has not been told. With ~3 weeks to the committed date, this disconnect is the most urgent item in the portfolio.

---

## Northstar Health — Nov 15 is not credible without immediate prioritization

**The commitment.** Nov 15 is the customer's expectation. The customer treats auditability and administrator controls as hard enterprise requirements, not preferences. Regulated healthcare environment.

**Two required capabilities, neither on a roadmap:**

- **Granular administrator permissions.** Product supports only Admin and User. Granular RBAC is "under consideration," not committed. Engineering has done early exploration only, with **no delivery date because it has not been prioritized**.
- **Customer-accessible audit history.** Activity is logged internally, but customers cannot export their own logs. Customer-facing audit export "would require additional engineering work" — no date.

**The approval chain is also stalled:**

- Security expects customer-facing audit evidence to be required before it grants production approval — so the missing audit-export capability is not just a product gap, it is a gate on Security sign-off.
- Compliance's regulatory assessment is open and **cannot progress until the security questionnaire is complete** — and that questionnaire is still in progress.

**Cross-functional read:** Nov 15 is ~10 weeks out. It depends on two capabilities that currently have no owner-committed date, no prioritization, and (per Engineering) no allocated capacity. The questionnaire → regulatory-assessment chain has also not started clearing. Without a prioritization decision this month, Nov 15 will slip.

---

## Mercury Retail — Q4 expansion rests on an uncommitted capability

**The commitment.** Account team reports the Q4 expansion across 14 European markets is on plan. The customer has already asked **when** granular administrator permissions will be available — meaning they are tracking this as a gating item.

**The dependencies:**

- The customer requires **separation between administrator roles**. Product offers a single Admin role. Admin-role separation is a form of the same granular RBAC capability that is unprioritized and undated for Northstar.
- EU data-governance review must complete before expansion. Compliance has started the assessment and reports no material findings yet — this is the one Mercury dependency actually moving.

**Cross-functional read:** The account team's "on plan" status depends on a capability that Engineering has not prioritized and cannot date. The customer is already asking for that date. The compliance track is progressing; the product/engineering track is not.

---

## Cross-cutting themes

**1. One capability decision unblocks two-and-a-half customers.**
Granular / separated administrator roles is a stated requirement for Northstar and Mercury, and is adjacent to GlobalBank's access-control expectations. It has had early engineering exploration but is not on the roadmap and has no capacity. This is the single highest-leverage prioritization decision in the portfolio.

**2. Automated provisioning is both a GlobalBank blocker and a broader regulated-enterprise exposure.**
It is the critical path for GlobalBank. Separately, Security notes that manual deprovisioning "may not meet access-control expectations for larger regulated enterprises" — which also implicates Northstar (regulated healthcare) even though Northstar has not raised provisioning explicitly yet.

**3. Customer-facing audit export appears in two places and is owned in neither.**
It is an explicit Northstar requirement, an expected Security precondition for Northstar approval, and undated in Engineering.

**4. Sales/account status is out of sync with internal reality across all three accounts.**
GlobalBank: "strong confidence," customer not informed of risk. Northstar: Nov 15 still "the customer expectation." Mercury: "on plan." In each case the external position is ahead of what Engineering, Security, and Compliance can currently support. GlobalBank is the acute case; the pattern is systemic.

**5. Every fix competes for capacity that does not exist.**
Engineering states no additional capacity is allocated. Provisioning, granular RBAC, and audit export cannot all be accelerated in parallel without a capacity or sequencing decision. Prioritizing one implicitly de-prioritizes the others.

---

## Decisions and escalations needed this week

1. **GlobalBank customer communication.** Align Sales, Security, and leadership on a revised GlobalBank date and a message to the customer. The Sep 30 date needs to be reset now, not after it is missed.
2. **RBAC prioritization.** Decide whether granular / separated admin roles enters the committed roadmap. Two active enterprise deals ($ + Q4 expansion) depend on it; today it has no date.
3. **Audit export prioritization.** Decide whether customer-facing audit export is committed for Northstar, and get Engineering a date. It gates both the product requirement and Security approval.
4. **Engineering capacity.** Leadership decision on whether to add capacity or explicitly sequence provisioning → RBAC → audit export. Without this, all three dates are aspirational.
5. **Northstar questionnaire.** Drive the in-progress security questionnaire to completion — it is the upstream blocker for the Compliance regulatory assessment.

---

## Watch list

- Engineering confidence in the Oct 15 provisioning date (currently *medium*, no buffer).
- Mercury EU data-governance assessment — currently clean; confirm it stays that way as scope covers 14 markets.
- Whether Northstar formally raises automated provisioning, given Security's general concern about manual deprovisioning in regulated environments.
