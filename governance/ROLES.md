# Community Roles — The Reef

This document defines the roles within The Reef, the official OpenOctopus community. Each role carries specific responsibilities, privileges, and expectations. Roles reflect the level of involvement and trust a community member has earned.

## Table of Contents

- [Role Overview](#role-overview)
- [Role Definitions](#role-definitions)
  - [1. Reef Dweller](#1-reef-dweller)
  - [2. Summoner](#2-summoner)
  - [3. Realm Builder](#3-realm-builder)
  - [4. Tentacler](#4-tentacler)
  - [5. Octo Core](#5-octo-core)
- [Promotion Paths](#promotion-paths)
- [Role Removal](#role-removal)
- [Recognition](#recognition)

## Role Overview

| Role | Color | Discord Tag | Summary |
|------|-------|-------------|---------|
| **Octo Core** | Purple `#6C3FA0` | `@Octo Core` | Core maintainers and project stewards |
| **Tentacler** | Cyan `#00D4AA` | `@Tentacler` | Active code contributors |
| **Realm Builder** | Ocean `#1E3A5F` | `@Realm Builder` | Realm package creators and domain experts |
| **Summoner** | Gold `#FFD700` | `@Summoner` | SOUL.md authors and Entity design specialists |
| **Reef Dweller** | Default | `@Reef Dweller` | Community members (default role) |

Roles are **additive** — a person can hold multiple roles simultaneously. For example, an @Octo Core member who also writes SOUL.md templates holds both @Octo Core and @Summoner.

## Role Definitions

### 1. Reef Dweller

**The foundation of The Reef.** Every community member starts here.

**How to obtain:**
- Join The Reef Discord server or participate in any OpenOctopus GitHub repository

**Responsibilities:**
- Follow the [Code of Conduct](../CODE_OF_CONDUCT.md)
- Use the appropriate Discord channels for discussions
- Be respectful and constructive in all interactions

**Privileges:**
- Access to all public Discord channels
- Ability to open GitHub issues and participate in discussions
- Ability to submit pull requests (subject to review)
- Participation in community events (Realm of the Week nominations, Summon of the Month submissions, AMAs)

**Expectations:**
- Familiarity with the [Code of Conduct](../CODE_OF_CONDUCT.md) and community rules
- Willingness to learn and engage constructively

---

### 2. Summoner

**Creative specialists who bring Entities to life through SOUL.md design.**

Summoners understand the art and craft of personality design, writing SOUL.md files that give Summoned Agents their unique character, memory patterns, and behavioral traits.

**How to obtain:**
- Share a creative and well-crafted SOUL.md in the [Soul Gallery](https://github.com/open-octopus/soul-gallery) (accepted via PR), **or**
- Consistently share high-quality Entity designs in the `#summon-showcase` Discord channel (at least 3 featured designs as recognized by an @Octo Core member)

**Responsibilities:**
- Maintain quality standards for SOUL.md templates in the Soul Gallery
- Provide constructive feedback on Entity designs shared by others
- Help newcomers understand SOUL.md writing techniques
- Participate in Summon of the Month judging when invited

**Privileges:**
- All Reef Dweller privileges
- `@Summoner` Discord role with gold color
- Featured author credit in the Soul Gallery
- Eligible to judge Summon of the Month competitions
- Access to the `#entity-design` channel as a recognized expert
- Invitation to SOUL.md design review discussions

**Expectations:**
- Active participation in Entity design discussions (at least monthly)
- Willingness to mentor new SOUL.md authors
- Adherence to SOUL.md quality guidelines

---

### 3. Realm Builder

**Domain experts who create complete Realm packages for the community.**

Realm Builders design and implement Realm packages — self-contained domain solutions that include Skills, configurations, and domain knowledge for specific life areas.

**How to obtain:**
- Publish a Realm package to [RealmHub](https://github.com/open-octopus/realmhub) (accepted via PR), **or**
- Make significant contributions to the [official Realms repository](https://github.com/open-octopus/realms) (at least 2 merged PRs with substantial domain logic)

**Responsibilities:**
- Maintain the Realm packages they have authored
- Respond to issues and PRs related to their Realm packages within a reasonable timeframe
- Follow the REALM.md specification and package structure standards
- Share domain expertise in the appropriate `#realm-*` Discord channels
- Help review other Realm package submissions

**Privileges:**
- All Reef Dweller privileges
- `@Realm Builder` Discord role with ocean color
- Listed as a Realm package author in RealmHub
- Priority review for new Realm package submissions
- Access to Realm Builder coordination channels
- Eligible for Realm of the Week nominations

**Expectations:**
- Maintenance of published Realm packages (bug fixes, compatibility updates)
- Active participation in Realm-related discussions (at least bi-weekly)
- Willingness to collaborate with other Realm Builders on cross-domain integrations

---

### 4. Tentacler

**Active code contributors who shape the technical direction of OpenOctopus.**

Tentaclers have demonstrated consistent, high-quality contributions to the OpenOctopus codebase. They are trusted members of the development community with deeper access and review responsibilities.

**How to obtain:**
- Have at least **3 non-trivial pull requests merged** in any OpenOctopus repository, **and**
- Demonstrate understanding of the project's architecture and conventions, **and**
- Be nominated by an existing @Octo Core or @Tentacler member

**Responsibilities:**
- Review pull requests from other contributors (aim for at least 2 reviews per month)
- Help triage GitHub issues (labeling, reproducing bugs, requesting more information)
- Maintain code quality standards in reviewed PRs
- Participate in technical discussions on GitHub and Discord
- Attend Dev Standup calls when possible (at least once per month)

**Privileges:**
- All Reef Dweller privileges
- `@Tentacler` Discord role with cyan color
- Write access to non-protected branches in OpenOctopus repositories
- Ability to approve and merge Tier 1 pull requests
- Ability to approve Tier 2 pull requests (merge requires @Octo Core)
- Listed as a contributor on the project README
- Invitation to Tentacler-only coordination channels

**Expectations:**
- Sustained contribution activity (at least 1 contribution per month — code, reviews, or issue triage)
- Adherence to all project conventions (conventional commits, TypeScript strict mode, test colocation)
- Responsiveness to review requests (within 72 hours)
- Mentorship of newer contributors

---

### 5. Octo Core

**Core maintainers and stewards of the OpenOctopus project.**

@Octo Core members are the leadership team responsible for the project's technical direction, governance, community health, and release management. They have the highest level of trust and responsibility.

**How to obtain:**
- Sustained, significant contributions over an extended period (typically 6+ months), **and**
- Deep understanding of the project architecture, goals, and community values, **and**
- Unanimous invitation from existing @Octo Core members

**Responsibilities:**
- Set and communicate the project's technical direction and roadmap
- Manage releases (CalVer versioning, changelog, npm publishing, Docker images)
- Moderate community spaces (Discord, GitHub) per the [Moderation Policy](MODERATION.md)
- Review and vote on RFCs
- Approve and merge Tier 2 and Tier 3 changes
- Handle Code of Conduct enforcement
- Mentor Tentaclers and other contributors toward greater responsibility
- Represent the project publicly (blog posts, conferences, social media)

**Privileges:**
- All Tentacler privileges
- `@Octo Core` Discord role with purple color
- Admin access to all OpenOctopus repositories
- Ability to merge any pull request
- Voting rights on RFCs and governance changes
- Access to private @Octo Core coordination channels
- Authority to grant and revoke community roles
- Release management permissions (npm, Docker Hub, GitHub Releases)

**Expectations:**
- Active involvement in project governance and decision-making
- Regular participation in Dev Standups and community events
- Timely response to security reports and critical issues (within 24 hours)
- Commitment to the project's long-term health and sustainability
- Fair and transparent enforcement of community policies

## Promotion Paths

The following diagram illustrates the typical progression through community roles:

```
Reef Dweller
    |
    |--- Share SOUL.md / Entity designs ---------> Summoner
    |
    |--- Publish Realm packages -----------------> Realm Builder
    |
    |--- Merge 3+ PRs + nomination --------------> Tentacler
                                                       |
                                                       |--- 6+ months sustained contribution
                                                       |    + unanimous @Octo Core invitation
                                                       |
                                                       v
                                                   Octo Core
```

### Cross-Role Progression

Roles are not mutually exclusive. Common multi-role paths include:

- **Summoner + Realm Builder:** Authors who design both Entity personalities and complete Realm packages
- **Tentacler + Realm Builder:** Developers who contribute code and also build Realm packages
- **Tentacler + Summoner:** Developers who also create notable SOUL.md templates
- **Octo Core + any combination:** Core team members often hold multiple roles

### Nomination Process

For roles requiring nomination (Tentacler, Octo Core):

1. A current role holder nominates the candidate in the private coordination channel
2. The nomination includes specific contributions and evidence of qualification
3. A discussion period of 7 days follows
4. For Tentacler: majority approval from @Octo Core members
5. For Octo Core: unanimous approval from existing @Octo Core members
6. The candidate is notified and publicly welcomed

## Role Removal

Roles may be removed under the following circumstances:

### Voluntary

A member may voluntarily step down from any role at any time by notifying an @Octo Core member. Stepping down is respected and carries no stigma.

### Inactivity

- **Tentacler:** No contributions (code, reviews, or issue triage) for 6 consecutive months. The member is contacted first and given 30 days to resume activity before role removal.
- **Octo Core:** No active participation for 3 consecutive months. The member is contacted privately and given the option to step down to Tentacler or take a formal leave of absence (up to 6 months).

### Conduct Violations

Serious or repeated violations of the [Code of Conduct](../CODE_OF_CONDUCT.md) may result in role removal as part of the enforcement process. See [MODERATION.md](MODERATION.md) for details.

### Reinstatement

Members who have had a role removed due to inactivity may be reinstated by demonstrating renewed activity and receiving approval from an @Octo Core member. The original contribution history is considered — the full qualification criteria need not be re-met from scratch.

## Recognition

OpenOctopus values every contribution. In addition to roles, contributors are recognized through:

- **Contributors page:** All contributors with merged PRs are listed on the project README and website
- **Release notes:** Contributors are credited in release changelogs
- **Realm of the Week:** Weekly showcase highlighting outstanding Realm contributions
- **Summon of the Month:** Monthly recognition for the best Entity/SOUL.md designs
- **Community spotlight:** Periodic blog posts or social media features highlighting notable contributors

---

*In a coral reef, every organism plays a vital role — from the microscopic algae that provide energy to the apex predators that maintain balance. The same is true of The Reef. Every role matters.*
