# Realm Builder Guide

A comprehensive guide to creating Realm packages for OpenOctopus and publishing them to RealmHub.

## What is a Realm?

A **Realm** is an autonomous life domain in OpenOctopus — like an octopus tentacle with its own nerve center. Each Realm encapsulates domain-specific knowledge, Skills, Agent configurations, and Entity templates for a particular area of life.

Examples of Realms:

| Realm | Domain | What It Does |
|-------|--------|-------------|
| Pet | Pet care | Vet appointment tracking, feeding schedules, health records |
| Finance | Personal finance | Budget tracking, expense categorization, tax reminders |
| Health | Health and fitness | Workout tracking, medication reminders, health metrics |
| Legal | Legal matters | Document management, deadline tracking, attorney notes |
| Family | Family management | Shared calendars, meal planning, family communication |
| Work | Professional life | Meeting management, project tracking, career development |

## What is a Realm Package?

A Realm package is a self-contained, distributable unit that defines everything needed for a specific Realm. Realm packages are shared through [RealmHub](https://github.com/open-octopus/realmhub) — the Realm marketplace.

A Realm package includes:

- **REALM.md** — The Realm definition file (required)
- **Skills** — Domain-specific capabilities (actions, queries, integrations)
- **Entity templates** — Pre-built Entity definitions with SOUL.md files
- **Configuration** — Default settings and customization options
- **Documentation** — Usage instructions and examples

## REALM.md File Format

The `REALM.md` file is the heart of every Realm package. It defines the Realm's identity, capabilities, and behavior.

### Structure

```markdown
# [Realm Name]

## Identity

- **Name:** [Human-readable name]
- **ID:** realm_[slug]
- **Version:** [CalVer: YYYY.M.D]
- **Author:** [Author name or GitHub username]
- **License:** [License identifier]
- **Description:** [One-paragraph description of the Realm]

## Domain

[Detailed description of the life domain this Realm covers. What problems does it solve?
What aspects of life does it manage? Who is the target user?]

## Skills

### Global Skills Used

[List of Global Skills this Realm depends on]

- `search` — Web search for domain-relevant information
- `calendar` — Calendar integration for scheduling
- `email` — Email notifications and summaries

### Realm Skills

[Domain-specific Skills provided by this Realm]

#### [Skill Name]

- **ID:** skill_[slug]
- **Type:** [action | query | integration]
- **Description:** [What this Skill does]
- **Input:** [Expected input parameters]
- **Output:** [What the Skill returns]

## Entities

[Pre-defined Entity templates included in this Realm]

### [Entity Template Name]

- **Type:** [living | asset | organization | abstract]
- **Description:** [What this Entity represents]
- **SOUL.md:** [Path to the SOUL.md file, e.g., `entities/pet.soul.md`]

## Configuration

[Default configuration options for this Realm]

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| [option_name] | [type] | [default] | [description] |

## Dependencies

[Other Realm packages or external services this Realm depends on]

- [dependency_name] — [why it's needed]

## Examples

[Usage examples showing how to interact with this Realm]
```

### Example: Pet Realm

```markdown
# Pet Care Realm

## Identity

- **Name:** Pet Care
- **ID:** realm_pet-care
- **Version:** 2026.3.1
- **Author:** @openoctopus
- **License:** MIT
- **Description:** A comprehensive Realm for managing pet care, including health records, feeding schedules, vet appointments, and behavioral tracking.

## Domain

The Pet Care Realm helps pet owners manage all aspects of their pets' lives. It covers
health management (vet visits, vaccinations, medications), daily care (feeding, grooming,
exercise), behavioral tracking, and emergency preparedness. Whether you have a dog, cat,
bird, or exotic pet, this Realm adapts to your specific needs.

## Skills

### Global Skills Used

- `calendar` — Scheduling vet appointments and care reminders
- `search` — Looking up pet health information
- `email` — Sending appointment confirmations

### Realm Skills

#### Vet Appointment Manager

- **ID:** skill_vet-appointment
- **Type:** action
- **Description:** Schedules, tracks, and reminds about veterinary appointments
- **Input:** Pet name, appointment type, date, vet clinic
- **Output:** Confirmation with calendar entry and reminders

#### Health Record Tracker

- **ID:** skill_health-record
- **Type:** query
- **Description:** Maintains and queries pet health history
- **Input:** Pet name, record type (vaccination, checkup, medication)
- **Output:** Health record entries with dates and notes

## Entities

### Pet Entity

- **Type:** living
- **Description:** Represents an individual pet with personality, health history, and care needs
- **SOUL.md:** `entities/pet.soul.md`

## Configuration

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| reminder_advance | number | 24 | Hours before appointment to send reminder |
| feeding_times | string[] | ["08:00", "18:00"] | Default feeding schedule times |
| vet_search_radius | number | 25 | Radius in km for vet clinic search |

## Dependencies

- None (standalone Realm)

## Examples

User: "Schedule a vet checkup for Momo next week"
Agent: "I've scheduled a checkup for Momo at Pawsome Vet Clinic next Wednesday at 10:00 AM.
        I'll remind you 24 hours before the appointment."
```

## Package Structure

A Realm package follows this directory structure:

```
realm-pet-care/
├── REALM.md              # Realm definition (required)
├── package.json          # Package metadata
├── src/
│   ├── index.ts          # Package entry point
│   ├── skills/
│   │   ├── vet-appointment.ts
│   │   ├── vet-appointment.test.ts
│   │   ├── health-record.ts
│   │   └── health-record.test.ts
│   ├── entities/
│   │   └── pet.soul.md
│   └── config.ts         # Default configuration with Zod schema
├── tsconfig.json
└── README.md             # Usage documentation
```

### package.json

```json
{
  "name": "@openoctopus/realm-pet-care",
  "version": "2026.3.1",
  "description": "Pet care Realm package for OpenOctopus",
  "main": "dist/index.js",
  "types": "dist/index.d.ts",
  "keywords": ["openoctopus", "realm", "pet", "pet-care"],
  "author": "Your Name",
  "license": "MIT",
  "peerDependencies": {
    "@openoctopus/shared": "*",
    "@openoctopus/core": "*"
  }
}
```

## Building a Realm Package

### Step 1: Plan Your Realm

Before writing code, define your Realm:

1. **Identify the domain:** What area of life does this Realm cover?
2. **Define the Skills:** What actions and queries should the Realm provide?
3. **Design the Entities:** What objects exist in this domain? What types are they (living, asset, organization, abstract)?
4. **Consider integrations:** Does this Realm need external APIs or services?

### Step 2: Write the REALM.md

Start with the REALM.md file. This is both the specification and documentation for your Realm. Follow the format described above.

### Step 3: Implement Skills

Each Skill is a TypeScript module that exports a Skill definition:

```typescript
import { defineSkill } from '@openoctopus/core';
import { z } from 'zod';

export const vetAppointmentSkill = defineSkill({
  id: 'skill_vet-appointment',
  name: 'Vet Appointment Manager',
  type: 'action',
  realm: 'realm_pet-care',
  inputSchema: z.object({
    petName: z.string(),
    appointmentType: z.enum(['checkup', 'vaccination', 'emergency', 'grooming']),
    date: z.string().datetime(),
    vetClinic: z.string().optional(),
  }),
  execute: async (input, context) => {
    // Skill implementation
  },
});
```

### Step 4: Create Entity Templates

Write SOUL.md files for pre-built Entity templates. See the [SOUL Author Guide](soul-author-guide.md) for detailed guidance on writing effective SOUL.md files.

### Step 5: Write Tests

Tests are colocated next to source files:

```typescript
import { describe, it, expect } from 'vitest';
import { vetAppointmentSkill } from './vet-appointment';

describe('vetAppointmentSkill', () => {
  it('should create an appointment with valid input', async () => {
    const result = await vetAppointmentSkill.execute({
      petName: 'Momo',
      appointmentType: 'checkup',
      date: '2026-04-01T10:00:00Z',
    }, mockContext);

    expect(result.success).toBe(true);
    expect(result.appointment.petName).toBe('Momo');
  });
});
```

Run tests with:

```bash
pnpm test:unit
```

### Step 6: Document Your Realm

Write a README.md that covers:

- What the Realm does
- How to install and configure it
- Usage examples
- Available Skills and their parameters
- Entity templates included

## Publishing to RealmHub

### Option A: Official Realms Repository

For Realm packages that meet quality standards and cover common use cases:

1. Fork the [realms repository](https://github.com/open-octopus/realms)
2. Add your Realm package to the appropriate directory
3. Submit a pull request with:
   - Complete REALM.md
   - Passing tests
   - Documentation
4. The @Octo Core team will review and merge

### Option B: Community Contribution

For experimental or niche Realm packages:

1. Publish your package to npm under your own scope or the `@openoctopus` scope (if approved)
2. Register it in the [RealmHub registry](https://github.com/open-octopus/realmhub)
3. The community can discover and install your Realm

### Quality Checklist

Before publishing, verify:

- [ ] REALM.md is complete and follows the standard format
- [ ] All Skills have input validation using Zod schemas
- [ ] Tests cover core functionality
- [ ] TypeScript strict mode — no `any` types or `@ts-ignore`
- [ ] All IDs follow the `{prefix}_{uuid}` format
- [ ] Documentation is clear and includes examples
- [ ] `pnpm check` passes
- [ ] `pnpm test:unit` passes

## Best Practices

### Design Principles

1. **Single domain focus.** A Realm should cover one coherent life domain. Avoid building a Realm that tries to do everything.
2. **Composable Skills.** Design Skills that can work independently and combine with other Skills — both within the Realm and across Realms.
3. **Sensible defaults.** Provide default configuration that works out of the box while allowing customization.
4. **Clear boundaries.** Define what is inside and outside the Realm's scope. Document dependencies on Global Skills or other Realms.

### Common Patterns

- **CRUD Skills:** Most Realms have Skills for creating, reading, updating, and deleting domain entities
- **Scheduling Skills:** Many Realms include time-based reminders and scheduling
- **Query Skills:** Skills that aggregate and summarize information from the Realm's knowledge base
- **Integration Skills:** Skills that connect to external APIs or services relevant to the domain

### Naming Conventions

- Realm IDs: `realm_[kebab-case-name]` (e.g., `realm_pet-care`)
- Skill IDs: `skill_[kebab-case-name]` (e.g., `skill_vet-appointment`)
- Entity IDs: `entity_[kebab-case-name]` (e.g., `entity_golden-retriever`)
- Package names: `@openoctopus/realm-[name]` (e.g., `@openoctopus/realm-pet-care`)

## Examples

Browse existing Realm packages for inspiration:

- [Official Realms](https://github.com/open-octopus/realms) — Maintained by the @Octo Core team
- [RealmHub Registry](https://github.com/open-octopus/realmhub) — Community-contributed Realms

## Getting Help

- **Discord:** Ask in `#dev-general` or the relevant `#realm-*` channel
- **GitHub:** Open an issue in the [realms repository](https://github.com/open-octopus/realms)
- **Dev Standup:** Bring questions to the bi-weekly developer call

---

*Each Realm is a territory of expertise — a tentacle reaching into a specific domain of life. As a Realm Builder, you are extending the reach of the octopus into new waters.*
