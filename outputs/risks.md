# Risk Register — Enterprise Readiness

Material enterprise-readiness risks only. Last reviewed: 2026-09-06.

**Severity** = impact on an enterprise commitment or security/regulatory/customer exposure
if unaddressed. **Evidence confidence** = how well the sources support this assessment.
These are independent: a High-severity risk can rest on Medium-confidence evidence when key
inputs (e.g. engineering effort) are still unknown.

Severity: High / Medium / Low. Evidence confidence: High / Medium / Low.

---

## R1 — GlobalBank September 30 date not met on the current plan
- **Customer(s):** GlobalBank
- **Capability:** Automated user provisioning (+ downstream Security and Compliance approval)
- **Dependency:** Provisioning GA (target Oct 15, medium confidence) → Security access-control review → Compliance production approval → customer security approval → production access
- **Severity:** High — $8M ACV, externally committed date ~24 days out
- **Evidence confidence:** High — dependency chain is explicit in the sources; Oct 15 falling after Sep 30 is arithmetic
- **Mitigation / unresolved path:** Re-baseline the date; OR customer waives provisioning as a production gate (not evaluated); OR Security accepts an interim compensating control and Compliance + customer approve in the window (not evaluated) — see D1, D3
- **Owner:** Product + Engineering leadership (date); Sales / exec sponsor (scope, customer); Security (interim control)

## R2 — GlobalBank customer is unaware of launch risk
- **Customer(s):** GlobalBank
- **Capability:** n/a — account communication
- **Dependency:** Agreed internal position (R1) → customer communication
- **Severity:** High — trust and possible contractual exposure on the largest account; worsens as the date nears
- **Evidence confidence:** High — sales.md states the customer has not been informed and holds strong confidence
- **Mitigation / unresolved path:** Sales-led communication once the internal position is set — see D2
- **Owner:** Sales / account leadership + executive sponsor

## R3 — Manual deprovisioning may not meet GlobalBank's control expectations
- **Customer(s):** GlobalBank (latent: Northstar)
- **Capability:** Automated de/provisioning
- **Dependency:** Manual deprovisioning until provisioning GA → Security access-control review evaluates it → possible findings and remediation
- **Severity:** Medium — could add findings and extend the timeline beyond R1's assumption
- **Evidence confidence:** Medium — security.md raises this as a general concern, not specifically for GlobalBank; also assumes provisioning scope includes deprovisioning
- **Mitigation / unresolved path:** Security decision on an interim compensating control; confirm provisioning scope covers deprovisioning — see D3
- **Owner:** Security

## R4 — Northstar November 15 at risk: granular administrator permissions uncommitted
- **Customer(s):** Northstar Health
- **Capability:** Granular RBAC *(shared — see portfolio)*
- **Dependency:** Prioritization → engineering effort estimate → delivery → requirement met; no capacity currently allocated
- **Severity:** High — regulated healthcare, customer treats it as a firm requirement; deal and renewal exposure
- **Evidence confidence:** Medium — that Nov 15 is threatened is well supported; the magnitude depends on an engineering effort estimate that does not yet exist
- **Mitigation / unresolved path:** Prioritize with a date and capacity; OR re-baseline Nov 15 — see D4, D6
- **Owner:** Product + Engineering leadership

## R5 — Northstar November 15 at risk: customer-facing audit export uncommitted
- **Customer(s):** Northstar Health
- **Capability:** Customer-facing audit export
- **Dependency:** Prioritization → engineering effort estimate → delivery; also a stated Security precondition for production approval
- **Severity:** High — blocks both the product requirement and Security approval
- **Evidence confidence:** Medium — threat is well supported; magnitude depends on an unknown effort estimate
- **Mitigation / unresolved path:** Prioritize with a date and capacity; OR re-baseline Nov 15 — see D5, D6
- **Owner:** Product + Engineering leadership

## R6 — Northstar regulatory assessment is blocked
- **Customer(s):** Northstar Health
- **Capability:** n/a — Compliance process dependent on the customer security questionnaire
- **Dependency:** Security questionnaire completed → Compliance regulatory assessment proceeds → regulatory approval
- **Severity:** Medium — compounds the Nov 15 risk; not independently deal-ending on current information
- **Evidence confidence:** High — compliance.md states the dependency explicitly
- **Mitigation / unresolved path:** Drive the questionnaire to completion; blocker owner not yet identified
- **Owner:** Compliance + Security; TPM to identify the questionnaire blocker owner

## R7 — Mercury Q4 expansion at risk: administrator-role separation undated
- **Customer(s):** Mercury Retail
- **Capability:** Granular RBAC — administrator-role-separation subset *(shared — see portfolio)*
- **Dependency:** Prioritization / scope decision → delivery; in parallel, EU data-governance review (in progress, no findings yet)
- **Severity:** Medium-High — 14-market expansion, customer already asking for a date; more runway than Northstar
- **Evidence confidence:** Medium — whether admin-role separation is separable from full RBAC is unknown; the exact Q4 deadline and any phasing are not stated
- **Mitigation / unresolved path:** Scope decision on a separable, scoped-down change; give the account team a date to share — see D4
- **Owner:** Product + Engineering leadership

## R8 — Engineering capacity constraint across competing enterprise work
- **Customer(s):** GlobalBank, Northstar Health, Mercury Retail
- **Capability:** Engineering capacity — automated provisioning, granular RBAC, customer-facing audit export
- **Dependency:** Capacity decision → sequencing → committed dates
- **Severity:** High — systemic; determines whether R1, R4, R5, and R7 are solvable at all
- **Evidence confidence:** High — engineering.md states no additional capacity is allocated
- **Mitigation / unresolved path:** Add capacity, or consciously sequence with aligned customer communications — see D6
- **Owner:** Engineering leadership + executive

## R9 — External commitments ahead of internal readiness on all three accounts
- **Customer(s):** GlobalBank, Northstar Health, Mercury Retail
- **Capability:** n/a — operating process
- **Dependency:** Per-account reconciliation (R1, R2, R4, R5, R7) + a joint readiness sign-off norm
- **Severity:** High — systemic; drives late discovery of slippage as the default failure mode
- **Evidence confidence:** High — both sides are documented per account in the sources
- **Mitigation / unresolved path:** Process norm requiring joint sign-off before external launch-date commitments — see D7
- **Owner:** Sales + Product / Engineering leadership; executive sponsor

---

## Severity vs. evidence-confidence summary

| Risk | Severity | Evidence confidence | Note |
|---|---|---|---|
| R1 GlobalBank date | High | High | Dependency math is explicit |
| R2 GlobalBank customer unaware | High | High | Stated in sales.md |
| R3 Manual deprovisioning | Medium | Medium | General concern, not GlobalBank-specific; scope assumption |
| R4 Northstar RBAC | High | Medium | Threat clear; magnitude needs effort estimate |
| R5 Northstar audit export | High | Medium | Threat clear; magnitude needs effort estimate |
| R6 Northstar assessment blocked | Medium | High | Dependency stated explicitly |
| R7 Mercury admin-role separation | Medium-High | Medium | Separability and Q4 date unknown |
| R8 Capacity constraint | High | High | No capacity allocated (stated) |
| R9 Commitments vs. readiness | High | High | Documented on all three accounts |
