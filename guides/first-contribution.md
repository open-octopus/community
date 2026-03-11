# Your First Contribution

A step-by-step guide to making your first pull request to OpenOctopus.

## Prerequisites

Before you begin, make sure you have:

- A [GitHub account](https://github.com)
- [Git](https://git-scm.com/) installed
- [Node.js](https://nodejs.org/) version 22 or later
- [pnpm](https://pnpm.io/) package manager installed
- A text editor or IDE (VS Code recommended)
- Basic familiarity with TypeScript and Git

## Step 1: Find an Issue

### Browse Good First Issues

Look for issues labeled `good-first-issue` in the OpenOctopus repositories:

- [Core repo good first issues](https://github.com/open-octopus/openoctopus/labels/good-first-issue)
- [Community repo good first issues](https://github.com/open-octopus/community/labels/good-first-issue)

### What Makes a Good First Issue

Good first issues typically involve:

- Fixing a typo or improving documentation
- Adding a missing test
- Fixing a small, well-defined bug
- Adding a small utility function
- Improving error messages

### Claim the Issue

Once you find an issue you want to work on:

1. Read the issue description and any linked discussions
2. Comment on the issue to let others know you are working on it
3. If the issue is unclear, ask questions in the issue comments or in `#dev-general` on Discord

## Step 2: Set Up the Development Environment

### Fork and Clone

```bash
# Fork the repository on GitHub (click the "Fork" button)

# Clone your fork
git clone https://github.com/YOUR_USERNAME/openoctopus.git
cd openoctopus

# Add the upstream remote
git remote add upstream https://github.com/open-octopus/openoctopus.git
```

### Install Dependencies

```bash
# Install all dependencies
pnpm install

# Build all packages
pnpm build

# Verify everything works
pnpm test:unit
```

If you encounter issues, check `#setup-help` on Discord.

### Understand the Monorepo Structure

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

The dependency graph flows: `shared -> storage, core -> summon, channels -> ink -> tentacle`

## Step 3: Create a Branch

```bash
# Make sure you are on the latest main
git checkout main
git pull upstream main

# Create a branch with the appropriate prefix
git checkout -b feat/your-feature-name
# or
git checkout -b fix/your-bug-fix
# or
git checkout -b docs/your-docs-change
```

### Branch Naming Conventions

| Prefix | Use Case |
|--------|----------|
| `feat/` | New features |
| `fix/` | Bug fixes |
| `docs/` | Documentation changes |
| `refactor/` | Code restructuring |
| `test/` | Test additions or improvements |
| `chore/` | Build/CI/tooling changes |

## Step 4: Make Your Changes

### Code Conventions

- **TypeScript strict mode** — no `@ts-ignore`, `@ts-nocheck`, or `any` type
- **ID format:** `{prefix}_{uuid}` (e.g., `realm_abc123-...`)
- **Schema validation:** Use Zod
- **Core terms in English:** Always write Realm, Entity, Summon, Agent, Skill in English

### Test Colocation

Tests live next to their source files:

```
src/
├── realm-manager.ts
├── realm-manager.test.ts     # <-- test file right next to source
├── entity-manager.ts
└── entity-manager.test.ts
```

### Writing Tests

```typescript
import { describe, it, expect } from 'vitest';

describe('YourModule', () => {
  it('should do the expected thing', () => {
    const result = yourFunction(input);
    expect(result).toBe(expectedOutput);
  });
});
```

## Step 5: Verify Your Changes

Before submitting, run the full verification suite:

```bash
# TypeScript type checking
pnpm typecheck

# Linting
pnpm lint

# Formatting
pnpm format

# Unit tests
pnpm test:unit

# All checks combined
pnpm check

# Dead code detection
pnpm knip
```

All checks must pass before you submit a PR.

## Step 6: Commit Your Changes

Use [Conventional Commits](https://www.conventionalcommits.org/) format:

```bash
# Stage your changes
git add <specific-files>

# Commit with a descriptive message
git commit -m "feat(core): add health realm skill registry"
```

### Commit Message Format

```
<type>(<scope>): <description>
```

- **type:** `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `chore`
- **scope:** The package name (`shared`, `storage`, `core`, `summon`, `channels`, `ink`, `tentacle`)
- **description:** A short, imperative description of the change

### Examples

```
feat(summon): add personality trait validation to SOUL.md parser
fix(storage): handle concurrent JSONL writes without corruption
docs(shared): add JSDoc comments to ID utility functions
test(core): add coverage for agent runner failover logic
```

## Step 7: Push and Create a Pull Request

```bash
# Push your branch to your fork
git push origin feat/your-feature-name
```

Then go to GitHub and create a pull request:

1. Navigate to your fork on GitHub
2. Click "Compare & pull request"
3. Set the base repository to `open-octopus/openoctopus` and the base branch to `main`
4. Fill in the PR template (see below)
5. Click "Create pull request"

### PR Template

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

## Step 8: Code Review

After submitting your PR:

1. **Wait for review.** An @Octo Core or @Tentacler member will review your PR, usually within a few days.
2. **Respond to feedback.** Address all review comments. If you disagree with a suggestion, explain your reasoning — respectful discussion is encouraged.
3. **Push updates.** If changes are requested, make them on the same branch and push:

```bash
git add <modified-files>
git commit -m "fix(core): address review feedback on skill registry"
git push origin feat/your-feature-name
```

4. **Request re-review.** After addressing all feedback, request a re-review from the reviewer.

## Step 9: Merge

Once your PR is approved:

- An @Octo Core member will merge it (squash-merge is the default strategy)
- Your changes will be included in the next release
- You will be credited in the changelog

Congratulations — you are now a contributor! After your first merged PR, you are on the path to earning the `@Tentacler` role.

## What is Next?

- **Keep contributing.** Pick up more issues, or find improvements on your own
- **Review others' PRs.** Reviewing code is a valuable contribution and helps you learn the codebase
- **Join the Dev Standup.** Bi-weekly voice calls are a great way to connect with other contributors
- **Explore other contribution types:**
  - [Build a Realm package](realm-builder-guide.md)
  - [Write a SOUL.md](soul-author-guide.md)
  - Help others in `#setup-help` or `#dev-general`

## Troubleshooting

### Common Issues

| Problem | Solution |
|---------|----------|
| `pnpm install` fails | Make sure you are using Node.js >= 22 and the latest pnpm |
| `pnpm build` fails | Try `pnpm clean && pnpm install && pnpm build` |
| Tests fail on a clean checkout | Ensure you have built all packages first: `pnpm build` |
| TypeScript errors in your IDE | Restart the TypeScript language server; ensure the project is built |
| CI checks fail but local checks pass | Make sure you are on the latest `main` and have pulled recent changes |

### Getting Help

- **Discord:** Ask in `#dev-general` or `#setup-help`
- **GitHub:** Comment on the issue you are working on
- **Code review:** Tag a specific person if your PR has been waiting more than 3 days

---

*Every journey across the ocean begins with a single stroke. Your first PR is that first stroke. Welcome aboard.*
