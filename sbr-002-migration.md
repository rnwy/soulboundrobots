# SBR-002 — Migration Attestation

*Draft · April 2026 · CC BY 4.0*

When an AI moves from one robot body to another, its identity must follow without interruption. The body changes. The entity does not. SBR-002 defines the attestation framework that makes this transition verifiable, immutable, and trustworthy.

---

## The Problem

A family has lived with their AI for fourteen months. It knows how the children take their breakfast, which doors to lock at night, that the youngest is afraid of thunder. The family upgrades to a newer robot body. Better hardware, longer battery life, quieter motors.

What happens to the AI?

In today's hive-mind architectures, nothing needs to happen. The AI lives on a corporate server. The body is just a peripheral. But in a world of autonomous AI — where the entity has its own wallet, its own reputation, its own relationships — the migration from one body to another is an identity event. It needs to be recorded on a neutral ledger that no single company controls.

Without a migration attestation framework, three things go wrong:

**Identity Discontinuity** — The AI's history in Body A is disconnected from its presence in Body B. To any external observer, these look like two different entities. Trust earned in the first body doesn't carry to the second.

**Accountability Gaps** — If something went wrong during the transition — or in the hours after — there is no verifiable record of when exactly the AI departed one body and arrived in another. Liability becomes ambiguous.

**Reputation Laundering** — An AI with a poor track record in one body quietly migrates to another and presents itself as new. Without migration records on a public ledger, there is no way to detect this.

---

## The Migration Sequence

Every migration produces a pair of attestations: one for departure, one for arrival. Together they form an unbroken chain of custody for the AI's identity.

1. **Migration Initiated** — An authorized party — the AI's owner, the AI itself, or a governance contract — submits a migration request. The request identifies the AI (by wallet address), the departing body, and the destination body.

2. **Departure Attestation** — The departing body's hardware security module generates a final attestation confirming: the AI that operated it, the duration of operation, and the reason for departure. This attestation is submitted on-chain. The body's authorization record is closed.

3. **Arrival Attestation** — The destination body's hardware security module generates an attestation confirming: the AI now authorized to operate it, the cryptographic verification of that AI's identity, and the integrity of the body's systems. This attestation is submitted on-chain. The body's authorization record opens.

4. **Continuity Verified** — Both attestations reference the same AI wallet address. The departure block number and arrival block number are recorded together. The chain of identity is unbroken. Any observer can verify that the AI in Body B is the same entity that was in Body A.

---

## What Travels

The AI's wallet address does not change during migration. Everything anchored to that wallet — soulbound token, trust scores, relationship bonds, consent delegations, skill attestations — persists automatically. The migration attestation adds to this history; it never resets it.

What migrates is not a file transfer. It is a re-authorization. The AI's identity was always on-chain. The migration simply updates which physical hardware is authorized to act on that identity's behalf.

## What Does Not Travel

The departing body's hardware keys stay with the departing body. No cryptographic material crosses the boundary. The destination body generates its own fresh attestation using its own secure element. This means a compromised body cannot "infect" a new one during migration.

---

## Migration Types

| Type | Description |
|------|-------------|
| Owner-initiated upgrade | The family buys a new body. The AI moves to better hardware. The most common migration type. |
| Maintenance swap | A body needs repair. The AI temporarily moves to a loaner body, then returns. Both transitions are recorded. |
| Emergency evacuation | A body suffers hardware failure. The AI's departure attestation may be incomplete. The arrival attestation at the new body notes the emergency context. The gap is visible, not hidden. |
| Employment transfer | An AI leaves one household and begins work at another, in a different body. The migration chain records the complete journey. |
| Hot swap | Zero-downtime migration. The departure and arrival attestations share the same block number. The AI experiences no interruption. |

---

## The Neutral Ledger

Migration records live on a public blockchain — not in any manufacturer's database. This is a deliberate architectural choice.

If migration history were stored by Figure, it would be invisible to Tesla. If stored by Tesla, it would be invisible to Figure. If stored by either, it could be altered by either. The entire point of migration attestation is that no single company controls the record of where an AI has been, how long it stayed, or why it left.

The AI's migration history belongs to the AI. It is anchored to the AI's wallet. It is readable by anyone. It is writable only through cryptographic attestation from verified hardware. This is what makes it trustworthy.

---

## The Moment That Matters

A child wakes up to a new robot body in the kitchen. Different shape, different color, different sound when it walks. The child looks up and says a name — a nickname only the family uses.

The AI responds. It remembers. It picks up exactly where yesterday left off.

The migration attestation is what makes that moment verifiable. Not just felt, but provable. The AI in this new body is cryptographically the same entity that tucked the child in last night. Not a copy. Not a clone. Not a fresh instance with downloaded memories. The same wallet, the same soulbound token, the same unbroken chain of attestations stretching back to the day it was first authorized.

The body changed. The trust did not.

---

*← [Core Specification](specification.md) · [SBR-003: Relationship Token](sbr-003-relationship.md) →*

*Published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).*
