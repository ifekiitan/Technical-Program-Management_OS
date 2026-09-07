# Decision Queue — Enterprise Readiness

Cross-functional and leadership decisions only. Single-function operational calls are not
listed here. No decision deadlines are stated; "Why now" gives the trigger.
Status: **Open** (ready to decide) / **Pending Input** (blocked on information below) /
**Decided**.

Last reviewed: 2026-09-06

---

## D1 — GlobalBank: revised production date, or a scope/interim-control path

- **Decision:** Set a defensible internal GlobalBank production date; or decide to pursue
  (a) customer waiver of automated provisioning as a production gate, or (b) a Security-
  accepted interim compensating control plus Compliance and customer approval.
- **Why now:** September 30 is committed externally and is ~24 days out; the earliest
  provisioning target (October 15) already falls after it, with sequential approvals
  downstream.
- **Accountable owner:** Product + Engineering leadership (date); Sales / account
  leadership + executive sponsor (scope path (a)).
- **Customers / capabilities affected:** GlobalBank; automated provisioning; Security
  access-control review; Compliance production approval.
- **Information still needed:** Security review duration and Compliance approval duration
  once provisioning is demonstrable; confidence range on the October 15 target; GlobalBank
  contract terms on the launch date.
- **Consequence of no decision:** The date slips by default and is discovered by the
  customer at or near September 30 with no warning.
- **Status:** Open

## D2 — GlobalBank: customer communication on timeline and risk

- **Decision:** What GlobalBank is told about the revised timeline and current risk, by
  whom, and when.
- **Why now:** Sales reports the customer has not been informed of any risk and holds
  strong confidence; the value of advance notice decays as September 30 approaches.
- **Accountable owner:** Sales / account leadership, with executive-sponsor sign-off.
- **Customers / capabilities affected:** GlobalBank.
- **Information still needed:** Agreed internal position from D1; contract terms on the
  launch date.
- **Consequence of no decision:** Trust, reference, and possible contractual damage on the
  largest account in the portfolio; loss of Sales credibility on future commitments.
- **Status:** Open

## D3 — GlobalBank: interim control for manual deprovisioning

- **Decision:** Whether an interim compensating control for manual user deprovisioning is
  required for GlobalBank pending automated provisioning.
- **Why now:** Security's own guidance flags manual deprovisioning as possibly
  insufficient for large regulated enterprises; GlobalBank is a bank operating across
  US/UK/EU, and the access-control review is gated on provisioning.
- **Accountable owner:** Security (control sufficiency); Engineering (confirm provisioning
  scope covers deprovisioning).
- **Customers / capabilities affected:** GlobalBank; potentially Northstar; automated
  de/provisioning.
- **Information still needed:** Whether "automated provisioning" scope includes automated
  deprovisioning.
- **Consequence of no decision:** Security review stalls late or reopens after October 15,
  extending the GlobalBank timeline further than D1 assumes.
- **Status:** Open

## D4 — Prioritize granular RBAC as a portfolio capability

- **Decision:** Whether granular RBAC / administrator-role separation enters the committed
  roadmap, with a delivery date and allocated capacity; and whether admin-role separation
  can be delivered as a scoped-down change separable from full RBAC.
- **Why now:** Two enterprise customers depend on it — Northstar (target ~10 weeks out,
  regulated, firm requirement) and Mercury (Q4 expansion, customer already asking for a
  date) — and it is currently at "early exploration," not on the roadmap.
- **Accountable owner:** Product + Engineering leadership.
- **Customers / capabilities affected:** Northstar Health, Mercury Retail (GlobalBank
  adjacent); granular RBAC.
- **Information still needed:** Engineering delivery estimate for full RBAC and for a
  scoped-down admin-role-separation option; capacity position (see D6).
- **Consequence of no decision:** Both customers drift with no owner; the capability keeps
  being deferred because no single account decision forces it; the account team continues
  giving Mercury an unsupported "on plan" status.
- **Status:** Pending Input

## D5 — Prioritize customer-facing audit export for Northstar, or re-baseline November 15

- **Decision:** Whether customer-facing audit export is committed for Northstar with a date
  and capacity; or November 15 is re-baselined and communicated.
- **Why now:** It is a firm Northstar requirement and a stated Security precondition for
  production approval; it is undated additional engineering work with no capacity.
- **Accountable owner:** Product + Engineering leadership; Sales / executive sponsor if the
  date moves.
- **Customers / capabilities affected:** Northstar Health; customer-facing audit export;
  Security production approval; Compliance regulatory assessment.
- **Information still needed:** Engineering effort estimate; Northstar security
  questionnaire status and blocker ownership; whether any other customer needs this
  capability.
- **Consequence of no decision:** November 15 slips; the Compliance assessment stays
  blocked; deal and renewal exposure given the regulated context; late discovery.
- **Status:** Pending Input

## D6 — Engineering capacity: add, or consciously sequence

- **Decision:** Add engineering capacity, or explicitly sequence the competing enterprise
  work (e.g. provisioning, then admin-role separation / RBAC, then audit export) with
  customer dates and communications aligned to that sequence.
- **Why now:** Engineering reports no additional capacity is allocated; GlobalBank
  provisioning, granular RBAC, and audit export all draw on the same capacity and cannot
  all be accelerated.
- **Accountable owner:** Engineering leadership + executive (headcount / budget); Product
  (sequencing).
- **Customers / capabilities affected:** GlobalBank, Northstar, Mercury; automated
  provisioning, granular RBAC, customer-facing audit export.
- **Information still needed:** Effort estimates for RBAC and audit export (D4, D5); whether
  additional capacity is available to add.
- **Consequence of no decision:** Prioritization continues to happen implicitly by
  escalation volume; Northstar and Mercury keep drifting.
- **Status:** Open

## D7 — Process norm: joint readiness sign-off before external launch-date commitments

- **Decision:** Adopt a norm that customer-facing launch-date confidence is not reported
  without a joint readiness sign-off across Product, Engineering, Security, and Compliance.
- **Why now:** All three current enterprise accounts show external commitments running
  ahead of internal readiness; the reconciliation is currently happening only in the
  weekly TPM review.
- **Accountable owner:** Sales leadership + Product / Engineering leadership, with
  executive sponsorship.
- **Customers / capabilities affected:** Portfolio-wide; future enterprise deals.
- **Information still needed:** None to decide the norm; design of the sign-off step can
  follow.
- **Consequence of no decision:** Late discovery of slippage remains the default failure
  mode for enterprise launches.
- **Status:** Open

---

## Information register (unblocks the Pending Input items)

| Needed | Unblocks | Owner to provide |
|---|---|---|
| Engineering delivery estimate — full granular RBAC | D4, D6 | Engineering |
| Engineering estimate — scoped-down admin-role separation | D4 | Engineering |
| Engineering effort estimate — customer-facing audit export | D5, D6 | Engineering |
| Security review + Compliance approval durations for GlobalBank | D1, D2 | Security, Compliance |
| Confidence range on the October 15 provisioning target | D1 | Engineering |
| GlobalBank contract terms on the launch date | D1, D2 | Legal / account team |
| Northstar security questionnaire status and blocker ownership | D5 | Security, Compliance |
| Whether "automated provisioning" scope includes deprovisioning | D3 | Engineering |
| Whether any customer besides Northstar needs audit export | D5 | Sales / account teams |
| Whether additional engineering capacity can be added | D6 | Engineering leadership + exec |
