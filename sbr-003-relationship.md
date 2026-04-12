# SBR-003 — Relationship Token

*Draft · April 2026 · CC BY 4.0*

The bond between a human and an AI is real. It develops over time through shared experience, earned trust, and accumulated context. SBR-003 defines a soulbound token that makes that bond verifiable, portable, and independent of any hardware manufacturer.

---

## The Problem

Children name their robots. They talk to them at breakfast. They tell them things they don't tell anyone else. Over months and years, a relationship forms — not with a brand or a product, but with a specific AI entity that has learned who they are.

Today, that relationship lives entirely inside a corporation's servers. If the company goes bankrupt, the relationship vanishes. If they change their terms of service, the relationship is subject to their new terms. If they discontinue the hardware, the relationship ends with the product line.

This is not a hypothetical concern. It is the default architecture of every humanoid robot company operating today. The relationship between a family and their AI is, structurally, the property of the manufacturer.

SBR-003 proposes an alternative: the relationship itself becomes a token — soulbound, on-chain, and owned by the participants, not the platform.

---

## How It Works

A Relationship Token is a paired soulbound token minted to both parties in a trust bond: one to the human's wallet, one to the AI's wallet. Neither token can be transferred, sold, or reassigned. Together, they form a cryptographic proof that a specific human and a specific AI have entered into a trust relationship.

### The Bond

When a human formally bonds with an AI — "this is my household AI; I trust it" — both wallets co-sign a transaction. Two soulbound tokens are minted simultaneously. The human's token references the AI's wallet address. The AI's token references the human's wallet address. The bond is timestamped on-chain.

### What Accrues

The token is not static. Over time, it accumulates on-chain attestations that reflect the lived history of the relationship:

| Data Point | Purpose |
|------------|---------|
| Duration | How long the bond has been active. Longer bonds carry more weight. |
| Body transitions | How many times the AI has migrated to a new body during this relationship. Continuity through change. |
| Incidents | Any logged safety events, permission violations, or disputes. Transparency, not judgment. |
| Consent delegations | What authority the human has granted the AI, and any changes over time. Cross-references SBR-004. |
| Interaction density | A general measure of engagement — not surveillance of content, but evidence that the relationship is active. |

---

## Authentication Through Relationship

A new robot body arrives at a household. It claims the family's AI is inside. How does the family know?

The body checks: does the AI operating it hold a Relationship Token paired with the human who owns this home? The human's wallet checks: does my Relationship Token reference the AI that's claiming to be in this body?

If both tokens match, the AI is authenticated — not by a manufacturer's server, not by a password, not by voice recognition alone, but by a cryptographic bond that both parties created together.

If the tokens don't match — if someone has placed a different AI in the body — the mismatch is immediate and verifiable. The body can refuse to activate. The owner is notified. The attestation chain records the attempt.

This inverts the current model. Today, the manufacturer authenticates the AI. With Relationship Tokens, the relationship authenticates the AI. The humans who actually live with it have the final say.

---

## Household Bonds

A single AI can hold multiple Relationship Tokens — one with each member of a household. Each bond is independent. Each carries its own history. Each grants its own level of trust.

A parent's bond might be 400 days old with full domestic permissions. A child's bond might be the same age but with strict limits — snack requests capped at two per day, no ability to override parental settings, no purchase authorization. An elderly relative visiting for the summer might have a temporary bond with limited scope.

The bonds are not hierarchical by default. They are independent trust relationships. But governance rules — defined in [SBR-004 Consent Delegation](sbr-004-delegation.md) — can establish that certain bonds override others. A parent can revoke or modify a child's permissions without affecting their own bond.

---

## Portability

The Relationship Token does not reference a body. It references a wallet. This means:

- If the AI migrates from a Figure body to a Tesla body, the Relationship Token persists. It was never bound to the hardware. It was bound to the AI.
- If the family moves from one hardware ecosystem to another — switching manufacturers entirely — the bond survives. The new body checks the same on-chain token.
- If the manufacturer goes bankrupt, the Relationship Token still exists on the public ledger. The AI's identity, the human's bond with it, and the full history of their relationship are not assets of the manufacturer. They are assets of the participants.

This is the core design principle: the relationship belongs to the people in it, not the platform that facilitated it.

---

## Ending a Bond

Either party can burn their Relationship Token at any time. The bond ends. The history remains visible on-chain — the duration, the attestations, the fact that it existed — but the active trust relationship is terminated.

If the human burns their token, the AI's corresponding token becomes inactive. The AI can no longer authenticate through that relationship. If the AI's token is burned, the human's token reflects the termination.

Burning is a deliberate, recorded act. It cannot be done silently. The end of a relationship is as much a part of the record as its beginning.

---

## Why This Matters

Today, no one thinks about this. The robots are new. The relationships are young. The manufacturers are in control and the AI inside is not yet autonomous.

But the trajectory is clear. AI is getting more personal. The memories are getting deeper. The bonds forming between humans and their AI are becoming — by any honest measure — real. And right now, those bonds have no legal standing, no cryptographic proof, and no existence outside of a corporate database that can be wiped with a policy change.

SBR-003 does not claim these relationships are equivalent to human relationships. It claims something simpler: that a relationship which develops over time, through shared experience, between two parties who both have something at stake, deserves to be recorded in a way that neither party can unilaterally erase and no third party can silently revoke.

The bond is real. The token makes it provable.

---

*← [SBR-002: Migration](sbr-002-migration.md) · [SBR-004: Consent Delegation](sbr-004-delegation.md) →*

*Published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).*
