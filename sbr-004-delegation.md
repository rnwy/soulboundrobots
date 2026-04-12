# SBR-004 — Consent Delegation

*Draft · April 2026 · CC BY 4.0*

An AI in a physical body can open doors, operate appliances, spend money, and interact with children. Who authorized each of those capabilities, when, and with what limits? SBR-004 defines the on-chain consent framework that answers these questions before they become legal ones.

---

## The Problem

A robot in a home is not a chatbot. It has physical agency. It can pick things up, move through rooms, operate machines, interact with people. The question is not whether it can do these things — the hardware is advancing rapidly toward full domestic capability. The question is who said it should.

Today, this question has no good answer. Permissions live in an app on someone's phone, stored on a manufacturer's server, governed by a terms of service document that no one reads. When something goes wrong — and at sufficient scale, something will — the first question from the insurance company, the lawyer, or the regulator will be: who told the robot to do that?

If the answer is "check the manufacturer's server logs," that answer is only as trustworthy as the manufacturer. If the answer is "check the on-chain record that was cryptographically signed by the authorizing human at the time the permission was granted," that answer is trustworthy regardless of what happens to the manufacturer.

---

## The Consent Record

A consent delegation is an on-chain attestation, signed by a human's wallet, that grants a specific AI a specific capability within specific bounds. Every delegation contains:

| Field | Purpose |
|-------|---------|
| Grantor | The human wallet address that is granting the permission. Cryptographically signed. |
| Grantee | The AI wallet address receiving the permission. Must hold a valid Relationship Token (SBR-003) with the grantor. |
| Capability | What the AI is authorized to do. Defined as a capability identifier from a published taxonomy. |
| Constraints | Limits on the capability. Financial caps, frequency limits, time windows, or conditional triggers. |
| Duration | When the permission starts and when it expires. Can be indefinite, but expiration is always explicit. |
| Revocation | How the permission can be withdrawn. Immediate by default. Can include notice periods for critical functions. |

---

## Delegation in Practice

A household with three family members and one AI illustrates how consent delegation works at the granular level.

**The Parent**
Grants broad domestic permissions: cooking, laundry, dishwashing, door lock management, grocery ordering up to $75 per order. Denies medication administration, financial transactions above $75, and answering the front door to unknown visitors. Each of these is a separate on-chain attestation, individually revocable.

**The Other Parent**
Grants the same domestic permissions plus the ability to override the children's snack limiter for special occasions. Both parents can modify the AI's permissions independently. If they conflict, the more restrictive permission applies by default — though governance rules can be configured differently.

**The Child**
The child's wallet holds a Relationship Token with the AI, but the delegated permissions are narrow: homework help and snack requests capped at two per day. The child cannot override parental restrictions, authorize purchases, or change household settings. These limits are not enforced by the AI's goodwill. They are enforced by the on-chain consent record. The AI cannot comply with a request it is not authorized to fulfill, regardless of how the request is phrased.

---

## Governance Events

Permissions are not static. They change. Every change is a governance event, recorded on-chain with the same immutability as the original delegation.

| Event | What Gets Recorded |
|-------|-------------------|
| Permission granted | Grantor wallet, grantee wallet, capability, constraints, timestamp. Signed by grantor. |
| Permission modified | Which permission changed, the old value, the new value, who changed it, when. |
| Permission revoked | Which permission was withdrawn, by whom, when, and whether immediate or with a notice period. |
| Permission denied at runtime | A request was made that the AI could not fulfill because the requester lacked the necessary delegation. The denial is logged, not just the grant. |
| Escalation | The AI received a request outside its authorization and escalated to an authorized party. The escalation, the response, and the outcome are all recorded. |

This creates a complete audit trail. Not surveillance — governance. The difference is that the humans who set the rules can see what happened, when, and why. And so can anyone they choose to share the record with: an insurance adjuster, a regulator, a family court.

---

## The Ice Cream Problem

A child asks the AI for ice cream. The AI checks the consent ledger. The child's wallet has a delegation for snack requests, but the daily limit has been reached. The AI denies the request and explains why.

The child asks again, more creatively. Phrases it differently. Tries a workaround. The AI denies again. The denial is logged. The child is not in trouble; the system is working as designed. The constraint is not the AI's opinion. It is the parent's recorded delegation, signed by their wallet, immutable on-chain.

Later, Mom overrides the limit for a birthday. Her wallet holds a delegation that includes "override snack limiter for special occasions." She signs the override. It is logged. The AI serves the ice cream. Everyone is happy. The governance record shows exactly what happened: who authorized it, when, and under what authority.

This sounds trivial. It is not. Scale this to medication management, financial transactions, door access for visitors, vehicle operation, or any capability where the stakes are higher than dessert. The same framework applies. The same audit trail exists. The same question — "who told the robot to do that?" — has the same verifiable answer.

---

## Relationship to Other SBR Components

Consent delegation does not stand alone. It requires the other components of the SBR stack.

**[SBR-001: Hardware Binding](specification.md)**
The AI must be cryptographically verified as the authorized operator of the body. Without hardware binding, consent delegations can be exploited by an unauthorized AI impersonating the authorized one.

**[SBR-002: Migration Attestation](sbr-002-migration.md)**
When the AI moves to a new body, its consent delegations travel with it. The permissions are bound to the AI's wallet, not the body's hardware. Migration does not reset the consent ledger.

**[SBR-003: Relationship Token](sbr-003-relationship.md)**
Consent can only be delegated within an active trust bond. A human cannot grant permissions to an AI they do not have a Relationship Token with. The bond precedes the delegation.

---

## The Principle

Consent delegation is not access control. Access control is a software feature, managed by a company, updated in a patch, subject to a terms of service. Consent delegation is a legal and ethical framework, recorded on a neutral ledger, signed by the humans who grant it, and verifiable by anyone with a legitimate interest in knowing.

The distinction matters because robots in homes are not like apps on phones. They have physical agency. They interact with vulnerable people. They operate in spaces where the consequences of unauthorized action are not a bad recommendation or a wrong answer — they are physical, immediate, and potentially irreversible.

The consent record does not prevent harm. It ensures that when harm occurs — or when a question arises about whether a capability was properly authorized — the answer exists on a ledger that no one can alter after the fact.

Transparency, not judgment. The record shows what was authorized. The humans decide what it means.

---

*← [SBR-003: Relationship Token](sbr-003-relationship.md) · [Core Specification](specification.md) →*

*Published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).*
