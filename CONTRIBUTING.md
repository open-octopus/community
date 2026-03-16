# Contributing to OpenOctopus

Thank you for your interest in contributing to OpenOctopus! Whether you are fixing a bug, building a Realm package, crafting a SOUL.md, or improving documentation, your contribution helps The Reef grow.

This guide covers the workflow, conventions, and expectations for all contributions.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [Terminology](#terminology)
- [Branch Naming](#branch-naming)
- [Commit Format](#commit-format)
- [Pull Request Process](#pull-request-process)
- [Code Conventions](#code-conventions)
- [Testing](#testing)
- [Documentation](#documentation)
- [Types of Contributions](#types-of-contributions)

## Code of Conduct

By participating in this project, you agree to abide by our [Code of Conduct](CODE_OF_CONDUCT.md). Please read it before contributing.

## Getting Started

1. **Fork** the repository you want to contribute to
2. **Clone** your fork locally
3. **Set up** the development environment (see below)
4. **Create a branch** from `main` with the appropriate prefix
5. **Make your changes** and test them
6. **Submit a pull request** using the PR template

## Development Setup

### Prerequisites

| Tool | Version | Purpose |
|------|---------|---------|
| Node.js | >= 22 | Runtime |
| pnpm | Latest | Package manager |
| Git | Latest | Version control |

### Installation

```bash
# Clone the core monorepo
git clone https://github.com/open-octopus/openoctopus.git
cd openoctopus

# Install dependencies
pnpm install

# Build all packages
pnpm build

# Run unit tests to verify setup
pnpm test:unit

# Run the full check suite
pnpm check
```

### Useful Commands

```bash
pnpm build              # Build all packages (8 packages)
pnpm dev                # Dev mode (ink gateway with hot-reload)
pnpm test:unit          # Run unit tests (51 tests)
pnpm test:integration   # Run integration tests
pnpm typecheck          # TypeScript project-reference build
pnpm lint               # oxlint
pnpm format             # oxfmt
pnpm knip               # Dead code detection
pnpm check              # typecheck + lint + format check
```

## Terminology

The five core terms **must always be written in English**, even in documents that are otherwise in another language:

| Term | Definition |
|------|-----------|
| **Realm** | An autonomous life domain (pet, finance, legal, health, etc.) |
| **Entity** | An object within a Realm — types: `living`, `asset`, `organization`, `abstract` |
| **Summon** | The process of transforming an Entity into a living AI Agent |
| **Agent** | An AI agent operating at one of three tiers: Central, Realm, or Summoned |
| **Skill** | A capability available to Agents — either Global or Realm-scoped |

## Branch Naming

All branches must use one of the following prefixes:

| Prefix | Use Case | Example |
|--------|----------|---------|
| `feat/` | New features or enhancements | `feat/realm-health-skills` |
| `fix/` | Bug fixes | `fix/session-jsonl-corruption` |
| `docs/` | Documentation changes | `docs/soul-author-guide` |
| `refactor/` | Code restructuring without behavior change | `refactor/storage-layer` |
| `test/` | Adding or improving tests | `test/agent-runner-coverage` |
| `chore/` | Build, CI, or tooling changes | `chore/update-tsdown-config` |

Branch names should be lowercase, use hyphens as separators, and be descriptive but concise.

## Commit Format

We use [Conventional Commits](https://www.conventionalcommits.org/) with the following format:

```
<type>(<scope>): <description>

[optional body]

[optional footer(s)]
```

### Types

| Type | Description |
|------|------------|
| `feat` | A new feature |
| `fix` | A bug fix |
| `docs` | Documentation only changes |
| `style` | Changes that do not affect the meaning of the code (formatting) |
| `refactor` | A code change that neither fixes a bug nor adds a feature |
| `perf` | A code change that improves performance |
| `test` | Adding missing tests or correcting existing tests |
| `chore` | Changes to the build process or auxiliary tools |

### Scopes

Scopes correspond to monorepo packages:

`shared`, `storage`, `core`, `summon`, `channels`, `ink`, `tentacle`, `realmhub`, `dashboard`

### Examples

```
feat(core): add health realm skill registry

fix(storage): prevent JSONL session corruption on concurrent writes

docs(summon): add SOUL.md personality trait examples

refactor(ink): extract WS RPC handler into separate module

test(shared): add ID format validation tests
```

## Pull Request Process

### Before Submitting

1. Ensure your branch is up to date with `main`
2. Run the full check suite: `pnpm check && pnpm test:unit`
3. Ensure no dead code is introduced: `pnpm knip`
4. Write or update tests for your changes

### PR Template

When you open a pull request, use the following template:

```markdown
## Summary

<!-- Brief description of what this PR does and why -->

## Type of Change

- [ ] Bug fix (non-breaking change that fixes an issue)
- [ ] New feature (non-breaking change that adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to change)
- [ ] Documentation update
- [ ] Refactoring (no functional changes)

## Related Issues

<!-- Link to related issues: Closes #123, Fixes #456 -->

## Changes

<!-- Bullet list of specific changes -->

## Testing

<!-- How were these changes tested? -->

- [ ] Unit tests added/updated
- [ ] Integration tests added/updated
- [ ] Manual testing performed

## Checklist

- [ ] My code follows the project's style guidelines
- [ ] I have performed a self-review of my own code
- [ ] I have commented my code in hard-to-understand areas
- [ ] I have updated documentation accordingly
- [ ] My changes generate no new warnings
- [ ] `pnpm check` passes
- [ ] `pnpm test:unit` passes
- [ ] `pnpm knip` reports no new dead code
- [ ] All IDs use the format `{prefix}_{uuid}`
- [ ] Tests are colocated next to source files (`*.test.ts`)
- [ ] The five core terms are written in English (Realm, Entity, Summon, Agent, Skill)
```

### Review Process

1. All PRs require at least one review from an **@Octo Core** or **@Tentacler** member
2. Trivial documentation fixes may be self-merged by **@Octo Core** members
3. Significant architectural changes require an RFC (see [Governance](governance/GOVERNANCE.md))
4. Address all review feedback before requesting re-review
5. Squash-merge is the default merge strategy

## Code Conventions

### TypeScript

- **Strict mode** is enabled — do not use `@ts-ignore`, `@ts-nocheck`, or the `any` type
- Use Zod for runtime schema validation
- Use the project's ID format: `{prefix}_{uuid}` (e.g., `realm_abc123-...`)
- Follow existing patterns — read the codebase before writing

### File Organization

- Tests are **colocated** next to source files with the `.test.ts` extension
- Each package has its own `src/` directory and `tsconfig.json`
- Exports go through each package's `src/index.ts`

### Monorepo Structure

```
packages/
├── shared/    — types, errors, IDs, logger, constants, config, RPC protocol
├── storage/   — SQLite, migrations, JSONL sessions, repos
├── core/      — realm manager, entity manager, agent runner, LLM providers
├── summon/    — SOUL.md parser, prompt compiler, summon engine
├── channels/  — channel adapters (Telegram, Discord, Slack, WeChat)
├── ink/       — Express+WS gateway, RPC handlers, API endpoints
├── tentacle/  — CLI tool with WS RPC streaming
├── realmhub/  — package registry client (Phase 3)
└── dashboard/ — Next.js web UI (Phase 2)
```

**Dependency graph:** `shared -> storage, core -> summon, channels -> ink -> tentacle`

### Naming Conventions

| Component | Name | Purpose |
|-----------|------|---------|
| CLI tool | `tentacle` | Command-line interface |
| Agent gateway | `ink` | Information flow medium (dual-port: WS 19789 + HTTP 19790) |
| Summon engine | `summon` | Entity summoning core |
| Channel system | `channels` | Messaging platform adapters |
| Realm marketplace | `RealmHub` | Domain package distribution |

## Testing

- **Framework:** Vitest 4 with V8 coverage
- **Test pool:** forks
- **Location:** Tests live next to their source files as `*.test.ts`
- **Run tests:** `pnpm test:unit`
- **Coverage:** Aim for meaningful coverage of business logic, not 100% line coverage

### Writing Tests

```typescript
import { describe, it, expect } from 'vitest';

describe('RealmManager', () => {
  it('should create a realm with valid ID format', () => {
    const realm = createRealm({ name: 'Pet Care' });
    expect(realm.id).toMatch(/^realm_[a-f0-9-]+$/);
  });
});
```

## Documentation

- Update documentation when your changes affect public APIs or user-facing behavior
- Use English for all technical documentation
- Reference the five core terms consistently
- Add JSDoc comments to exported functions and types

## Types of Contributions

### Code Contributions

Fix bugs, add features, improve performance, or refactor existing code in the core monorepo.

### Realm Packages

Create domain-specific Realm packages for [RealmHub](https://github.com/open-octopus/realms). See the [Realm Builder Guide](guides/realm-builder-guide.md).

### SOUL.md Templates

Design creative Entity personalities for the [Soul Gallery](https://github.com/open-octopus/soul-gallery). See the [SOUL Author Guide](guides/soul-author-guide.md).

### Documentation

Improve guides, fix typos, translate content, or write tutorials.

### Community

Help others in Discord, report bugs, suggest features, or participate in community events.

---

## Questions?

- **Discord:** [discord.gg/mwNTk8g5fV](https://discord.gg/mwNTk8g5fV) — ask in `#dev-general`
- **GitHub Discussions:** Open a discussion in the relevant repository
- **Email:** hello@openoctopus.club

Welcome to The Reef. Every contribution, no matter the size, sends ripples across the ocean.
