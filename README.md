# VPN Subscription System

An anonymized commercial engineering case study by Tommy. I worked on a network client and the account, checkout, renewal, and entitlement flows around it, using AI-assisted development.

**Public material:** documentation and conceptual diagrams. The commercial application, client identity, infrastructure, and business data remain private.

[繁體中文](README.zh-TW.md) · [Architecture and decisions](docs/architecture.md) · [Verification scope](docs/verification.md) · [Portfolio](https://github.com/asdc163/ai-builder-portfolio)

## The product problem

A user needs to choose a connection location, understand their subscription, pay, and return to the client with the right access. The difficult cases happen between those screens: partial payment, a delayed transfer, a renewal before expiry, or a service restart during confirmation.

## My work

I worked across product scope, the client experience, subscription and payment-state implementation, failure handling, and engineering handoff. The engineering included a Swift/SwiftUI iOS client, Node.js services, and a browser checkout flow. Earlier browser-client work had a narrower browser-only routing scope.

## Decisions that mattered

- Give each order its own payment destination so attribution does not depend on recognizing a shared amount.
- Keep exact received amounts in the ledger while making the next payment action readable for a person.
- Apply a confirmed payment once, including after repeated checks or a restart.
- Separate the capacity to open new orders from the ability to reconcile existing ones.
- Route late or uncertain payments to review without quietly reassigning them.

A renewal also has to preserve the user's remaining time. A payment status page and an entitlement record must agree about what has actually been granted.

## Recorded delivery state

The private project records describe automated backend checks, controlled checkout journeys, iOS simulator checks, and an unsigned device-target build. This public case was checked against those records on 2026-10-27; the commercial application was not rerun for this publication.

Production hosting and nodes, real funds, Apple signing, physical-device operation, and regional network availability require separate acceptance. This case makes no claim of a publicly available VPN service or verified use on a restricted network.

## What this demonstrates

Subscription lifecycle design, payment reconciliation, client/backend coordination, and a handoff that makes unresolved release work visible. AI assisted the development process; a model is not required for the payment or access decisions described here.

There is no runnable commercial code or customer demo in this repository. See [disclosure boundaries](DISCLOSURE.md) before reusing or requesting material.
