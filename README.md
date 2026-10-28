# VPN subscription system

A commercial network-client build with account, checkout and renewal flows. I worked on the product flow, Swift/SwiftUI client, Node.js services, payment state and engineering handoff.

A user should be able to pay, return to the client and see the correct subscription. Partial payments, late transfers and restarts make that harder than the screens suggest.

[繁體中文](README.zh-TW.md) · [Architecture](docs/architecture.md) · [Delivery notes](docs/delivery-decisions.md)

## Keep the ledger exact and the next action readable

Each order has its own payment destination. The ledger preserves the actual received amount, including partial or excess funds. The interface explains the next action without changing the accounting record to make the display simpler.

Once a confirmed payment has updated the subscription, repeated checks or a restart must not grant another period. Early renewals also retain the user's remaining time.

## Existing orders still need reconciliation

An exhausted address pool can stop new orders while existing ones still need payment checks. I separated those states so capacity changes would not hide an already-open checkout.

Late or uncertain funds retain a review path. They are not silently reassigned to a different order or treated as another renewal.

## Delivery status

The handoff includes controlled backend and checkout checks, iOS simulator work and an unsigned device-target build. Production infrastructure, real funds, signing and target-network acceptance remain separate steps in [validation notes](docs/verification.md).

An earlier browser-client version had browser-only routing scope. It is distinct from the native client described here.

Commercial code, client identity and operating data stay private. This public case contains documentation and conceptual diagrams. Development was AI-assisted; payment and access decisions use deterministic rules. [Disclosure](DISCLOSURE.md)
