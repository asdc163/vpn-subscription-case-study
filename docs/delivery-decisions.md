# Delivery decisions for a TPM discussion

This page reorganizes the existing anonymized engineering case around decisions, dependencies, and acceptance. It does not add a deployment claim or disclose private topology.

## State the delivery boundary

The engineering package connects the client, subscription state, checkout, payment observation, and entitlement application. A compiled client and a prepared service package are intermediate artifacts. A usable production release still depends on controlled infrastructure, funds reconciliation, signing, and real-device/network acceptance.

## Decisions and their consequences

| Decision | Consequence for the delivery | Acceptance question |
| --- | --- | --- |
| Attribute payments to an order-specific destination | Client guidance, address allocation, observation, and the ledger must agree. | Can a receipt be claimed by another account or applied again after restart? |
| Preserve exact received amounts | Human-facing guidance and accounting representation have different jobs. | Does partial or excess payment retain the original amount and a clear next action? |
| Separate order admission from existing-order reconciliation | Exhausted creation capacity need not hide an already-open payment path. | Can an existing order still be checked when new creation is blocked? |
| Preserve remaining subscription time on renewal | Entitlement calculation depends on the account's current term. | Does early renewal extend the term without discarding remaining time? |
| Keep exceptional funds visible for review | The operator must own an unresolved path. | Are late or uncertain receipts preserved without silently granting unrelated access? |

## Dependency and responsibility map

| Boundary | What needs to be available | Who must accept it |
| --- | --- | --- |
| Client ↔ account state | A consistent status contract and refresh behavior. | Client/service implementers and the recipient operator. |
| Observation ↔ ledger ↔ entitlement | Controlled receipt identity and durable application state. | Payment-system implementer and authorized funds operator. |
| Client ↔ network service | Deployed service configuration and target-environment checks. | Infrastructure operator and client tester. |
| Build ↔ distribution | Signing and installation through an authorized distribution path. | Distribution owner and device tester. |

These are responsibility categories, not named stakeholders or a historical team structure.

## Verification and handoff

The [verification summary](verification.md) records historical controlled backend, checkout, simulator, build, and packaging evidence. The recipient must separately accept production infrastructure, actual funds handling, signed device operation, and target-network behavior. The next decision is tied to the missing layer, not the count of passing local checks.

No schedule, budget, team size, adoption, or revenue result is asserted here. The technical contribution described is the implementation and delivery reasoning documented in the case.
