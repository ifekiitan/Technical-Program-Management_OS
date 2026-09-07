# Enterprise Readiness Portfolio

Portfolio-level view across customers and functions. Last reviewed: 2026-09-06.
Cross-references: `decisions.md` (D#), `risks.md` (R#).

---

## 1. Enterprise customers — overall readiness

| Customer | Target | Overall readiness | Headline blocker | Risks |
|---|---|---|---|---|
| **GlobalBank** | Sep 30 (prod) | **Date will not be met on current plan; launch recoverable on a revised date** | Automated provisioning targeted Oct 15; Security review and Compliance approval gated behind it; customer not yet informed | R1, R2, R3 |
| **Northstar Health** | Nov 15 (prod) | **At risk under the current plan** | Two firm requirements — granular admin permissions and customer-facing audit export — are unprioritized and undated; regulatory assessment blocked on an incomplete questionnaire | R4, R5, R6 |
| **Mercury Retail** | Q4 (14-market EU expansion) | **At risk under the current plan** | Administrator-role separation is undated; compliance (EU data-governance) track is progressing, product/engineering track is not | R7 |

---

## 2. Shared capability gaps vs. customer-specific issues

The distinction that matters for prioritization: a **shared capability gap** is one missing
platform capability that several customers need — it warrants one deliberate prioritization
decision. A **customer-specific issue** is contained to one account and does not generalize.

### Shared capability gaps

| Capability | Customers affected | Portfolio gap? | Status | Decision |
|---|---|---|---|---|
| **Granular RBAC / admin-role separation** | Northstar (*"granular administrator permissions"*), Mercury (*"separation between administrator roles"*); GlobalBank adjacent | **Yes — 2+ customers** | Early technical exploration only; not on roadmap; no capacity | D4 |
| **Customer-facing audit export** | Northstar (explicit requirement + Security approval precondition) | **Not yet — 1 customer.** Same shape as RBAC (internal capability exists; customer-facing surface does not). Promote if a 2nd customer appears | Undated additional engineering work | D5 |
| **Automated user provisioning / deprovisioning** | GlobalBank (mandatory for production); latent for Northstar via Security's regulated-enterprise deprovisioning concern | **Customer-specific today, latent portfolio exposure** | SSO GA and complete; automated provisioning not GA, target Oct 15, medium confidence, no capacity | D1, D3 |

### Customer-specific issues

| Issue | Customer | Why it does not generalize |
|---|---|---|
| Provisioning delivery timing + Security/Compliance sequencing + customer communication | GlobalBank | Tied to one customer's committed date and one production mandate |
| Security questionnaire incomplete → regulatory assessment blocked | Northstar | Customer-supplied questionnaire; specific to this engagement |
| EU data-governance review before expansion | Mercury | Specific to this expansion; in progress, no findings yet |

---

## 3. External commitments inconsistent with internal readiness

| Account | External commitment / signal | Internal readiness | Risk |
|---|---|---|---|
| GlobalBank | Sep 30 committed externally; customer not informed of risk; account team reports strong customer confidence | Provisioning target Oct 15 (medium); Security review open and gated; Compliance gated on Security | R1, R2 |
| Northstar Health | Nov 15 is the customer's expectation; auditability and admin controls treated as firm enterprise requirements | Both capabilities unprioritized and undated; security questionnaire in progress; regulatory assessment blocked | R4, R5, R6 |
| Mercury Retail | Q4 expansion reported "on plan" by the account team | Required admin-role separation is uncommitted and undated; customer already asking for availability | R7 |

Pattern: 3 of 3 accounts. The reconciliation between external commitment and internal
readiness is currently happening only in the weekly TPM review — see systemic issue S2.

---

## 4. Systemic operating issues

| # | Issue | Evidence | Consequence if unaddressed | Decision |
|---|---|---|---|---|
| **S1** | No engineering capacity allocated; provisioning, RBAC, and audit export compete for the same capacity | engineering.md — "no additional engineering capacity is currently allocated" | Prioritization happens implicitly by escalation volume, not by decision; Northstar and Mercury drift | D6 |
| **S2** | External commitments run ahead of internal readiness on every account | sales.md vs. product/engineering/security/compliance across all three | Late discovery of slippage becomes the default failure mode for enterprise launches | D7 |
| **S3** | No joint readiness sign-off gate before customer-facing launch-date commitments | Implied by S2; account teams commit dates without a cross-functional check | The pattern recurs on the next cohort of enterprise deals | D7 |

---

## 5. Missing information that could materially change prioritization

| Unknown | What it would change | Owner to provide |
|---|---|---|
| Engineering effort estimates for granular RBAC and for customer-facing audit export | Whether Northstar Nov 15 and Mercury Q4 are recoverable; how to sequence the work | Engineering |
| Whether admin-role separation is separable from full RBAC | Mercury's path and the scope of the RBAC decision (D4) | Engineering |
| Whether engineering capacity can be added | Whether the competing work can run in parallel or must be sequenced (D6) | Engineering leadership + exec |
| Whether any customer besides Northstar needs customer-facing audit export | Whether audit export becomes a portfolio capability gap (promote from Section 2) | Sales / account teams |
| Security review + Compliance approval durations for GlobalBank | Feasibility and shape of a revised GlobalBank date (D1) | Security, Compliance |
| GlobalBank contract terms on the launch date | Urgency and seniority of the GlobalBank customer conversation (D2) | Legal / account team |
| Legal and Support readiness (absent from all source inputs) | Mercury EU expansion likely has a Legal/DPA component; three enterprise launches in one quarter is an unassessed Support load — either could add gating items | Legal, Support |
