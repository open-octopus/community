# Dev Standup

A bi-weekly voice call for OpenOctopus developers to share progress, discuss blockers, and demo new features.

## Overview

| Detail | Value |
|--------|-------|
| **Frequency** | Every other Tuesday |
| **Time** | 17:00 UTC (30 minutes) |
| **Channel** | `Dev Standup` voice channel on Discord |
| **Organizer** | Rotating @Octo Core member |
| **Open to** | All contributors and community members |

## Purpose

The Dev Standup is a lightweight, regular sync for the development community. It provides:

- A structured opportunity to share what you have been working on
- A place to raise blockers and get help
- A window into what others are building across the monorepo
- A chance to demo features, get feedback, and coordinate efforts
- A way for newer contributors to learn about active development areas

## Format

The standup follows a fixed 30-minute agenda. The facilitator (a rotating @Octo Core member) keeps time and ensures everyone has a chance to speak.

### Agenda Template

```
Dev Standup — [Date]
Facilitator: @[username]

1. Roll Call (2 min)
   - Who is here? Quick wave/greeting.

2. Round Robin Updates (15 min)
   - Each participant shares:
     - What I worked on since last standup
     - What I plan to work on next
     - Any blockers or questions
   - Keep each update to 1-2 minutes

3. Demos (8 min)
   - Anyone with a feature, fix, or prototype to show
   - Screen sharing encouraged
   - Keep demos focused and concise

4. Open Discussion (5 min)
   - Cross-cutting topics
   - Coordination needs
   - Upcoming release planning
   - Event announcements
```

### Time Management

- If more than 10 people attend, updates may be limited to those with active contributions since the last standup
- Demos are first-come, first-served — post in `#dev-general` before the standup to reserve a demo slot
- If discussion on a topic runs long, the facilitator will suggest moving it to `#dev-general` or a separate call

## Participation

### Who Should Attend

The standup is open to everyone, but is most valuable for:

- **@Octo Core** members (expected to attend when possible)
- **@Tentacler** members (encouraged to attend at least once per month)
- **@Realm Builder** members working on active packages
- Any community member actively contributing code, documentation, or Realm packages

### How to Join

1. Go to the `Dev Standup` voice channel on Discord at the scheduled time
2. No RSVP is required — just show up
3. If you cannot attend, you can post your update asynchronously in `#dev-general` before the standup

### First-Time Attendees

If it is your first standup, welcome! You do not need to have an update ready. Listening is a perfectly valid form of participation. Feel free to introduce yourself during the roll call.

## Notes

### Taking Notes

A designated note-taker (the facilitator or a volunteer) captures key points during the standup.

### Notes Format

```markdown
# Dev Standup Notes — [YYYY-MM-DD]

**Facilitator:** @[username]
**Attendees:** @[user1], @[user2], @[user3], ...

## Updates

### @[user1]
- **Done:** [summary of completed work]
- **Next:** [planned work]
- **Blockers:** [any blockers, or "None"]

### @[user2]
- **Done:** [summary]
- **Next:** [planned work]
- **Blockers:** [any blockers]

## Demos

### [Demo Title] — @[username]
- [Brief description of what was demonstrated]
- [Key feedback or questions raised]

## Discussion

- [Topic 1]: [summary of discussion and any decisions]
- [Topic 2]: [summary]

## Action Items

- [ ] @[username]: [action item description]
- [ ] @[username]: [action item description]
```

### Publishing Notes

After each standup, the notes are:

1. Posted in `#dev-general` on Discord
2. Stored in the `standup-notes/` directory of the community repository (if applicable)
3. Referenced in the next standup for continuity

## Schedule

The standup occurs every other Tuesday. The schedule for the current quarter is pinned in `#dev-general`.

### Schedule Changes

If a standup needs to be rescheduled (holiday, conflict):

- The facilitator posts a notice in `#dev-general` at least 48 hours in advance
- An alternative date/time is proposed
- The standup is never skipped entirely — it is rescheduled or held asynchronously

### Async Standup (Fallback)

If a voice standup cannot be held, an asynchronous standup is conducted in `#dev-general`:

1. The facilitator posts the standup thread with the agenda template
2. Participants post their updates as replies within 24 hours
3. Discussion happens in the thread

## Facilitator Rotation

The facilitator role rotates among @Octo Core members on a bi-weekly basis. The rotation schedule is maintained in a pinned message in `#dev-general`.

### Facilitator Responsibilities

- Post a reminder in `#dev-general` 24 hours before the standup
- Open the voice channel and start the meeting on time
- Follow the agenda and keep time
- Take or delegate note-taking
- Post notes after the standup

---

*Regular check-ins keep the current flowing. The Dev Standup is where individual streams of work converge into a shared direction.*
