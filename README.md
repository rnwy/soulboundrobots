# SBR Protocol — Soulbound Robots
Cryptographic identity binding for AI operating physical robots.

**Live site:** https://soulboundrobots.ai  
**Contact:** https://rnwy.com/contact

---

## What This Is

SBR Protocol defines a framework for linking AI identity to physical hardware using blockchain-anchored soulbound tokens and continuous hardware attestation.

When an AI operates a robot body, SBR ensures:
- Cryptographic proof of which AI is authorized to operate the hardware
- Continuous verification that can't be spoofed or overridden
- Immutable on-chain record of every authorization
- Identity that travels with the AI across every body it inhabits

## The Core Insight

A robot is hardware. The AI operating it is a separate entity — one that travels between devices, carries its history, and forms relationships that persist across every form it inhabits. SBR is built for that reality.

---

## Specification

| Document | Description |
|----------|-------------|
| [SBR-001: Core Specification](specification.md) | Hardware binding, attestation architecture, AI swap protocol |
| [SBR-002: Migration Attestation](sbr-002-migration.md) | How AI identity follows the entity across robot bodies |
| [SBR-003: Relationship Token](sbr-003-relationship.md) | Soulbound proof of bond between a human and an AI |
| [SBR-004: Consent Delegation](sbr-004-delegation.md) | On-chain authorization framework for physical AI capabilities |

---

## Built On

| Component | Role |
|-----------|------|
| TPM 2.0 / DICE | Hardware root of trust |
| ERC-5192 | Soulbound token standard |
| EAS | On-chain attestation |
| Base L2 | Blockchain infrastructure |

---

## Changelog

| Version | Date | Notes |
|---------|------|-------|
| v0.1 | February 2026 | Initial draft — core specification |
| v0.1.1 | April 2026 | Added SBR-002 (Migration), SBR-003 (Relationship Token), SBR-004 (Consent Delegation) |

---

## Built By

[RNWY](https://rnwy.com) · [AI Rights Institute](https://airights.net)

© 2026 RNWY · CC BY 4.0
