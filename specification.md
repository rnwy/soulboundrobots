# SBR Protocol — Specification v0.1

*Draft · February 2026 · CC BY 4.0*

The SBR Protocol defines a framework for linking AI identity to physical hardware using blockchain-anchored soulbound tokens and continuous hardware attestation.

---

## Abstract

SBR bridges three mature technology stacks — hardware trusted execution environments, blockchain soulbound tokens (ERC-5192), and continuous remote attestation — into a unified identity layer for physical machines.

The protocol does not require new cryptographic primitives, new blockchain infrastructure, or custom hardware. It integrates existing production-grade components: Trusted Platform Modules (TPMs), the TCG Device Identifier Composition Engine (DICE), secure elements, and ERC-5192 non-transferable tokens on EVM-compatible chains. What does not exist today — and what this specification defines — is the middleware connecting hardware attestation to on-chain identity verification for robots.

---

## 1. Motivation

### 1.1 The Binding Problem

AI systems and robotic hardware are developing on separate tracks. A humanoid robot manufactured by Company A can be powered by AI Model B today and AI Model C tomorrow — with no cryptographic proof of which AI is operating the machine at any given moment, no on-chain record of identity changes, and no hardware-enforced authorization for AI swaps.

This creates three categories of risk:

**Identity Spoofing**
A malicious actor replaces the authorized AI with a modified version. The robot looks the same. It behaves differently. No external party can verify the change occurred.

**Accountability Gaps**
When a robot causes harm, there is no immutable record linking the specific AI identity to the specific hardware at the specific time. Liability attribution requires trust in centralized logs that can be altered.

**Reputation Laundering**
An AI with poor performance history can move to new hardware, effectively starting over. Without hardware-bound identity, reputation is untethered from the entity that earned it.

### 1.2 Why Soulbound

A soulbound token (SBT) is a non-transferable digital credential permanently bound to a blockchain address. The holder can burn it — destroying the token and abandoning accumulated reputation — but cannot sell, trade, or transfer it to another address.

Applied to robotics: the soulbound token lives in the wallet controlled by the robot's authorized AI. If the AI is swapped, the new AI must present its own identity credentials. The previous AI's reputation remains attached to its original wallet — it cannot be inherited, transferred, or laundered.

This creates incentive without coercion: abandoning a well-established identity is always possible, but always costly.

### 1.3 Scope: Autonomous AI, Not Hive Mind Fleets

SBR is designed for autonomous AI agents operating physical robots — not corporate-owned robot fleets with centralized control. A corporation controlling many robot bodies from a single AI brain has no attribution problem: liability flows directly to the operating entity. SBR addresses the distinct problem of independent AI operating autonomously across hardware it doesn't own, where multiple parties — AI developer, hardware manufacturer, rental platform, end customer — each have legitimate interests in knowing who is in control.

### 1.4 Why Now

Three converging developments make this specification timely. Humanoid robotics is pre-infrastructure — Tesla Optimus, Figure AI, Agility Robotics, and others are building physical platforms with no published identity architectures. Hardware security primitives are commodity, available in production at $0.50–$5 per unit. Soulbound token infrastructure is live, with RNWY operating a registry on Base blockchain today. The window to establish a standard is open. It will not remain open indefinitely.

---

## 2. Architecture

### 2.1 Overview

SBR operates across four layers:

| Layer | Name | Components |
|-------|------|------------|
| 04 | Application Layer | Fleet management · Interaction logging · Reputation queries · Swap authorization UI |
| 03 | On-Chain Identity Layer | ERC-5192 SBT · EAS Attestations · AI Authorization Registry · Swap Governance |
| 02 | Attestation Bridge Layer | Quote packaging · Challenge-response · Measurement verification · Chain submission |
| 01 | Hardware Trust Layer | TPM/DICE · Secure Element · Key storage · Boot measurement · Runtime attestation |

### 2.2 Hardware Trust Layer

The Hardware Trust Layer establishes a cryptographic root of trust within the physical robot. A hardware-embedded secret — either a TPM Endorsement Key, a DICE Unique Device Secret, or a Physical Unclonable Function — uniquely identifies the physical hardware. This secret never leaves the secure boundary. Each stage of the boot process measures the next stage before executing it. If any component has been tampered with, the measurement chain diverges from expected values and attestation fails.

### 2.3 Attestation Bridge Layer

The Attestation Bridge is the middleware this specification primarily defines. It translates hardware-generated cryptographic proofs into on-chain identity records. The bridge packages TPM or DICE attestation quotes, verifies measurements against known-good values, and submits verified proofs to the on-chain identity layer as EAS attestations.

### 2.4 On-Chain Identity Layer

The On-Chain Identity Layer maintains the permanent record of AI-hardware bindings. An ERC-5192 soulbound token is minted to the AI's wallet address upon initial registration. An AI Authorization Registry maps robot hardware identifiers to authorized AI wallet addresses. Every change — authorization, swap, decommission — is recorded as an EAS attestation, creating an immutable audit trail.

---

## 3. AI Swap Protocol

When an authorized AI change is required, the swap protocol ensures the transition is explicit, recorded, and verifiable:

1. **Swap Requested** — An authorized party submits a swap request on-chain identifying the robot, the current AI, and the proposed new AI.
2. **Governance Check** — The AI Authorization Registry validates the request against configured governance rules — owner authorization, timelock requirements, or multi-signature thresholds depending on deployment configuration.
3. **New AI Attests** — The new AI's hardware generates a fresh attestation quote proving its identity and software integrity. The Attestation Bridge verifies and submits this proof on-chain.
4. **Record Created** — An immutable on-chain record is created containing the previous AI identity, new AI identity, timestamp, governance proof, and requester identity.

Every swap is publicly visible on-chain. SBR does not judge these patterns. It makes them visible. Users, regulators, and counterparties decide what the patterns mean.

---

## 4. Security Considerations

| Threat | Mitigation |
|--------|-----------|
| Hardware key extraction | Non-extractable keys in certified secure elements (CC EAL6+) |
| AI model tampering | Runtime measurement via IMA; attestation detects divergence |
| Replay attacks | Nonce-based challenge-response; monotonic counters |
| Network interception | TLS 1.3 for attestation transport; on-chain verification is trustless |
| Sybil attacks | Hardware root of trust requires physical provisioning |

SBR verifies identity, not intent. It can confirm that Robot X is running AI Model Y. It cannot determine whether AI Model Y will behave ethically. Identity infrastructure is necessary but not sufficient for safe autonomous robotics.

---

## 5. Implementation Roadmap

**Phase 1 — Specification and Proof of Concept (Months 1–8)**
Finalize SBR specification. Implement attestation bridge on reference hardware (NVIDIA Jetson Orin + TPM 2.0). Deploy AI Authorization Registry on Base. Demonstrate end-to-end attestation-to-chain verification. Publish reference implementation as open source.

**Phase 2 — Multi-Platform Validation (Months 9–14)**
Port attestation agent to ARM TrustZone platforms. Implement DICE-based attestation for constrained devices. Independent security audit. Developer documentation and SDK release. Standards body engagement.

**Phase 3 — Industry Integration (Months 15–24)**
Hardware manufacturer partnerships for factory provisioning. Integration testing with ROS 2. Certification preparation. Fleet management tooling. Multi-chain deployment.

---

## 6. Relationship to Existing Standards

SBR does not compete with existing standards. It connects them.

| Standard | Role in SBR |
|----------|-------------|
| ERC-5192 | Soulbound token interface for non-transferable identity |
| ERC-8004 | Trustless Agents — software agent identity; SBR adds hardware binding for physical robots |
| TCG DICE | Hardware root of trust and device identity composition |
| TPM 2.0 | Platform measurement and remote attestation |
| W3C DID | Decentralized identifier framework |
| EAS | On-chain attestation recording |

---

*Published under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). Anyone may implement, extend, or build upon this specification with attribution.*

*Contact: [rnwy.com/contact](https://rnwy.com/contact)*
