# OpenOctopus Governance

This document describes the governance model for the OpenOctopus project. It covers how decisions are made, how significant changes are proposed and adopted, and how releases are managed.

## Table of Contents

- [Principles](#principles)
- [Decision-Making Process](#decision-making-process)
- [RFC Mechanism](#rfc-mechanism)
- [Release Flow](#release-flow)
- [Monorepo Governance](#monorepo-governance)
- [Community Input](#community-input)

## Principles

OpenOctopus governance is guided by the following principles:

1. **Transparency** — Decisions are made in the open. Discussions happen in public channels (GitHub issues, Discord, RFCs) wherever possible.
2. **Meritocracy** — Influence is earned through sustained, high-quality contributions. See [ROLES.md](ROLES.md) for the role hierarchy and promotion paths.
3. **Pragmatism** — We favor working solutions over perfect ones. Ship, iterate, improve.
4. **Inclusivity** — All community members can participate in discussions and propose changes, regardless of their role.
5. **Autonomy** — Each Realm of the project operates with appropriate independence, mirroring the domain autonomy that defines the product itself.

## Decision-Making Process

Decisions fall into three categories based on their scope and impact:

### Tier 1: Minor Changes — Direct Merge

**Scope:** Typo fixes, minor documentation updates, small bug fixes, test additions, dependency updates.

**Process:**
1. Open a pull request
2. Get at least one approval from an **@Octo Core** or **@Tentacler** member
3. Merge

**Timeline:** Same day to a few days.

### Tier 2: Standard Changes — Lazy Consensus

**Scope:** New features within existing architecture, non-breaking API changes, new Skill implementations, new channel adapters, package refactoring.

**Process:**
1. Open a GitHub issue describing the proposed change
2. Allow 72 hours for discussion and objections
3. If no objections are raised by an **@Octo Core** member, the change is approved (lazy consensus)
4. Implement and submit a pull request
5. Get at least one approval from an **@Octo Core** member
6. Merge

**Timeline:** 3-7 days.

### Tier 3: Significant Changes — RFC Required

**Scope:** New packages in the monorepo, architectural changes, breaking API changes, new core concepts, changes to the governance model, new community policies, major dependency changes.

**Process:** See the [RFC Mechanism](#rfc-mechanism) below.

**Timeline:** 2-4 weeks.

## RFC Mechanism

RFC (Request for Comments) is the process for proposing and adopting significant changes to OpenOctopus.

### RFC Lifecycle

```
Draft -> Proposal -> Discussion -> Vote -> Accepted/Rejected -> Implementation
```

### 1. Draft

The author creates a new RFC document following the template below and opens a pull request to the `rfcs/` directory of the core repository.

**RFC Template:**

```markdown
# RFC-XXXX: [Title]

- **Author:** [GitHub username]
- **Date:** [YYYY-MM-DD]
- **Status:** Draft
- **Category:** [core | summon | channels | ink | tentacle | governance | community]

## Summary

One paragraph description of the proposal.

## Motivation

Why is this change needed? What problem does it solve?

## Detailed Design

Technical details of the proposed change. Include:
- API changes
- Data model changes
- Migration strategy
- Impact on existing packages

## Alternatives Considered

What other approaches were evaluated and why were they rejected?

## Drawbacks

What are the potential downsides of this approach?

## Unresolved Questions

What aspects of the design are still to be determined?
```

### 2. Proposal

Once the author is satisfied with the draft, they label the PR as `rfc:proposal` and announce it in:
- The `#dev-general` Discord channel
- The relevant GitHub Discussion category

### 3. Discussion

A minimum discussion period of **7 calendar days** is required. During this time:
- Any community member can comment on the RFC PR
- The author is expected to respond to feedback and update the RFC accordingly
- **@Octo Core** members may request specific changes before proceeding to a vote

### 4. Vote

After the discussion period, an **@Octo Core** member initiates a vote:
- **Eligible voters:** All **@Octo Core** members
- **Voting period:** 5 calendar days
- **Threshold:** Simple majority of active @Octo Core members (those who have contributed in the last 90 days)
- **Voting options:** Approve, Reject, Abstain

### 5. Outcome

- **Accepted:** The RFC is merged and moves to implementation. The author or a volunteer implements the change.
- **Rejected:** The RFC PR is closed with a summary of reasons. The author may revise and resubmit.
- **Deferred:** The RFC is valid but not a current priority. It remains open for future consideration.

### 6. Implementation

The accepted RFC is implemented through standard pull requests. The RFC document is updated with:
- Implementation PR links
- Any deviations from the original design
- Final status: `Implemented`

## Release Flow

OpenOctopus uses **CalVer** (Calendar Versioning) with the format `YYYY.M.D`.

### Versioning

| Format | Example | Description |
|--------|---------|-------------|
| `YYYY.M.D` | `2026.3.11` | Standard release |
| `YYYY.M.D-beta.N` | `2026.3.11-beta.1` | Pre-release / beta |
| `YYYY.M.D-rc.N` | `2026.3.11-rc.1` | Release candidate |

### Release Process

1. **Release branch:** A release branch `release/YYYY.M.D` is created from `main`
2. **Stabilization:** Only bug fixes are cherry-picked into the release branch
3. **Testing:** Full test suite passes, integration tests verified
4. **Changelog:** `CHANGELOG.md` is updated with all changes since the last release
5. **Tag and publish:** The release is tagged, Docker images are built, npm packages are published
6. **Announcement:** Release notes are posted to `#announcements` on Discord and GitHub Releases

### Release Cadence

- **Regular releases:** As needed, roughly every 2-4 weeks during active development
- **Hotfix releases:** Same-day for critical security or data-loss bugs
- **Major milestones:** Aligned with the project roadmap (Phase 1, Phase 2, Phase 3)

### Monorepo Releases

All packages in the monorepo share the same version number. When a release is cut, all 8 packages are published together:

```
@openoctopus/shared
@openoctopus/storage
@openoctopus/core
@openoctopus/summon
@openoctopus/channels
@openoctopus/ink
@openoctopus/tentacle
@openoctopus/realmhub
```

## Monorepo Governance

Each package in the monorepo may have designated maintainers who have deeper context on that area:

| Package | Area |
|---------|------|
| `shared` | Types, errors, IDs, logger, constants, config, RPC protocol |
| `storage` | SQLite, migrations, JSONL sessions, repos |
| `core` | Realm manager, entity manager, agent runner, LLM providers, router |
| `summon` | SOUL.md parser, prompt compiler, summon engine |
| `channels` | Channel adapters (Telegram, Discord, Slack, WeChat) |
| `ink` | Express+WS gateway, RPC handlers, API endpoints |
| `tentacle` | CLI tool with WS RPC streaming |
| `realmhub` | Package registry client |

Package maintainers have the authority to approve Tier 1 and Tier 2 changes within their package. Cross-package changes require @Octo Core approval.

## Community Input

All community members are encouraged to participate in governance:

- **GitHub Issues:** Report bugs, suggest features, ask questions
- **GitHub Discussions:** Longer-form conversations and proposals
- **Discord `#ideas`:** Informal feature brainstorming
- **Discord `#dev-general`:** Technical discussion
- **RFC process:** Formal proposals for significant changes
- **Community events:** Dev Standups, AMAs, and other events are opportunities to voice opinions

The governance model itself is subject to change through the RFC process. Proposals to modify governance require a two-thirds majority vote from @Octo Core members.

---

*Good governance, like a healthy reef, creates the conditions for life to flourish on its own terms.*
