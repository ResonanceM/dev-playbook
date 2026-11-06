# Technical Debt: Identify, Quantify, and Pay Down Deliberately

Technical debt is a trade-off that creates future cost or risk. Not all shortcuts are harmful; debt becomes dangerous when its interest is invisible or unmanaged.

## Debt taxonomy

- **Deliberate/prudent:** conscious shortcut with a repayment plan.
- **Deliberate/reckless:** knowingly skips essential design or quality controls.
- **Inadvertent/prudent:** learning reveals a better design after implementation.
- **Inadvertent/reckless:** poor understanding or weak engineering practice creates avoidable complexity.

Also classify debt by domain: architecture, code, tests, data, security, infrastructure, dependencies, documentation, and operational process.

## Prioritization

Assess:
- User/business impact.
- Frequency of change in the affected area.
- Delivery drag and rework.
- Incident/security/compliance exposure.
- Cost of remediation and migration risk.
- Confidence in the evidence.

A useful heuristic is debt interest: how much extra time, risk, or incident cost does this debt create each time the team touches the area?

## Portfolio approach

Do not apply a universal “20% rule” without evidence. Reserve capacity based on observed maintenance burden, risk, and strategic investment. Combine:
- Opportunistic cleanup in touched code.
- Targeted remediation for high-interest debt.
- Planned platform/architecture investments.
- Mandatory security and lifecycle work.

## Negotiating with product

Translate debt into consequences: slower lead time, higher defect probability, support burden, outage exposure, or inability to meet a product requirement. Offer options: pay now, contain risk, or accept a documented consequence.

## Debt register

| Item | Impact/interest | Evidence | Remediation | Cost | Owner | Review |
|---|---|---|---|---|---|---|
| Unsupported runtime | Security and upgrade risk | Vendor lifecycle | Upgrade in stages | M | Platform | Quarterly |

Keep the register small and actionable. Archive items that no longer matter.

## Guardrails

- Do not label every refactor “debt.”
- Do not optimize code without a user, reliability, security, or delivery reason.
- Do not defer end-of-life dependencies indefinitely.
- Track outcomes after remediation.
