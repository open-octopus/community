# Discord Server Setup Guide

Complete guide to setting up and configuring The Reef — the official OpenOctopus Discord community server.

## Server Basics

| Setting | Value |
|---------|-------|
| **Server Name** | The Reef |
| **Description** | Official community for OpenOctopus — the realm-native life agent system |
| **Invite Link** | `discord.gg/openoctopus` (Vanity URL, requires Boost Level 3) |
| **Languages** | English (primary), Chinese welcome |

## Creating the Server

1. Discord → Left sidebar "+" → Create My Own → For a community
2. Enter Server Name: `The Reef`
3. Upload Server Icon: use `openoctopus-avatar.png` from `docs/assets/`
4. After creation → Server Settings → Overview → Upload Banner

### Enable Community Features

1. Server Settings → Enable Community
2. Set Rules Channel: `#rules`
3. Set Updates Channel: `#announcements`
4. Enable Welcome Screen

### Welcome Screen

```
Welcome to The Reef!

The official OpenOctopus community.
Organize life by realms. Summon anything into a living agent.
```

**Recommended channel highlights (max 5):**

| Channel | Description |
|---------|-------------|
| `#rules` | Community rules — read these first |
| `#general` | Casual discussion, anything goes |
| `#showcase` | Show off your Realm and Summon creations |
| `#dev-general` | Developer discussion |
| `#setup-help` | Installation and usage questions |

## Channel Structure

### INFO (Read-Only)

| Channel | Type | Permissions | Purpose |
|---------|------|-------------|---------|
| `#rules` | Text | Read-only | Community rules |
| `#announcements` | Announcement | Read-only | Official announcements, release notes |
| `#roadmap` | Text | Read-only | Development roadmap and progress |

### GENERAL

| Channel | Purpose |
|---------|---------|
| `#general` | Casual discussion |
| `#introductions` | New member introductions |
| `#showcase` | Share your Realm configs, Summon screenshots, experiences |
| `#ideas` | Feature suggestions and discussion |
| `#off-topic` | Non-project chat |

### REALMS (Domain Discussion)

| Channel | Topic |
|---------|-------|
| `#realm-pet` | Pet Realm discussion |
| `#realm-family` | Family / parenting / relationships |
| `#realm-finance` | Finance and budgeting |
| `#realm-work` | Work and productivity |
| `#realm-legal` | Legal domain |
| `#realm-health` | Health and fitness |
| `#realm-custom` | Custom Realm discussion |

### SUMMON

| Channel | Topic |
|---------|-------|
| `#summon-showcase` | Show off your Summoned Entities |
| `#entity-design` | Discuss Entity design, SOUL.md writing, personality tuning |
| `#summon-ideas` | Summon feature ideas and requests |

### DEV (Development)

| Channel | Topic |
|---------|-------|
| `#dev-general` | General developer discussion |
| `#tentacle-cli` | CLI tool development |
| `#ink-gateway` | Agent gateway development |
| `#realmhub` | RealmHub marketplace |
| `#contributions` | PR discussion, code review |

### HELP

| Channel | Type | Topic |
|---------|------|-------|
| `#setup-help` | Text | Installation and configuration |
| `#bug-reports` | Text | Bug reports |
| `#feature-requests` | Forum | Feature requests with threaded discussion |

### VOICE

| Channel | Purpose |
|---------|---------|
| General Voice | Casual voice chat |
| Dev Standup | Bi-weekly developer standup meetings |

## Roles

| Role | Color | Hex | Description |
|------|-------|-----|-------------|
| @Octo Core | Purple | `#6C3FA0` | Core team maintainers |
| @Tentacler | Teal | `#00D4AA` | Active code contributors |
| @Realm Builder | Navy | `#1E3A5F` | Realm package creators |
| @Summoner | Gold | `#FFD700` | Active Entity/SOUL.md creators |
| @Reef Dweller | Default | — | Community members (default) |

### Role Permissions

| Permission | Octo Core | Tentacler | Realm Builder | Summoner | Reef Dweller |
|-----------|-----------|-----------|---------------|----------|--------------|
| Manage Server | Yes | No | No | No | No |
| Manage Channels | Yes | No | No | No | No |
| Manage Roles | Yes | No | No | No | No |
| Kick/Ban Members | Yes | No | No | No | No |
| Manage Messages | Yes | Yes | No | No | No |
| Create Threads | Yes | Yes | Yes | Yes | Yes |
| Send Messages | Yes | Yes | Yes | Yes | Yes |
| Post in Announcements | Yes | No | No | No | No |
| Use Voice Channels | Yes | Yes | Yes | Yes | Yes |

## Bot Configuration

### Recommended Bots

| Bot | Purpose |
|-----|---------|
| **Carl-bot** or **MEE6** | Auto-role assignment, leveling system, welcome messages |
| **GitHub Bot** | Sync GitHub notifications to `#announcements` |
| **Disboard** | Community discovery and listing |

### Welcome Message Template

Configure your welcome bot to send:

```
Welcome to The Reef, {user}!

You've just entered the OpenOctopus community.

Quick start:
- Read the #rules first
- Introduce yourself in #introductions
- Check out #showcase to see what others are building
- Devs: head to #dev-general

SUMMON!
```

### GitHub Webhook Setup

1. Go to the GitHub repository → Settings → Webhooks → Add webhook
2. Payload URL: Discord Webhook URL (from `#announcements` channel settings → Integrations → Webhooks)
3. Content type: `application/json`
4. Events to trigger: Releases, Issues, Pull Requests

## Community Rules (for #rules channel)

Post the following in `#rules`:

```
The Reef — Community Rules

1. Be respectful. Treat others as you would treat a friendly octopus.
2. Stay on topic. Use the right channel for your message.
3. No spam, self-promotion, or advertising without permission.
4. No NSFW content.
5. Help others. Share knowledge, not judgement.
6. English and Chinese are both welcome.
7. Report issues to @Octo Core or use ModMail.

Violations: warning → mute → ban.

SUMMON responsibly!
```

## Moderation Setup

1. Enable AutoMod (Server Settings → AutoMod)
   - Block commonly flagged words
   - Block mention spam (5+ mentions)
   - Block spam content
2. Set up ModMail or a `#mod-log` channel for the @Octo Core team
3. Review [MODERATION.md](../governance/MODERATION.md) for enforcement guidelines

## Growth Strategy

1. **README badge:** Add a Discord invite badge to all GitHub READMEs
2. **GitHub → Discord:** Direct deeper discussions from GitHub Issues to Discord
3. **Showcase incentives:** Feature outstanding showcases in GitHub README and social media
4. **Automatic roles:** RealmHub contributors automatically receive @Realm Builder
5. **Cross-platform:** Share Discord highlights on X / social media

## Maintenance

- Review and prune inactive channels quarterly
- Update roles and permissions as the community grows
- Rotate pinned messages in active channels monthly
- Archive seasonal event channels after completion
