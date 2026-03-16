# Discord Server Setup Guide

Complete guide to setting up and configuring The Reef — the official OpenOctopus Discord community server.

## Server Basics

| Setting | Value |
|---------|-------|
| **Server Name** | The Reef |
| **Description** | Official community for OpenOctopus — the realm-native life agent system |
| **Invite Link** | `discord.gg/openoctopus` (Vanity URL, requires Boost Level 3) |
| **Languages** | English |

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

### 📋 INFO

| Channel | Topic |
|---------|-------|
| `#start-here` | New here? Project overview, quick links, and how to navigate this server |
| `#rules` | Community rules and code of conduct. Please read before participating |
| `#announcements` | Official project updates and releases. Low-volume, high-signal |
| `#roadmap` | Development roadmap and milestone tracking |

### 💬 GENERAL

| Channel | Topic |
|---------|-------|
| `#general` | Casual discussion about OpenOctopus. For support questions, use #setup-help |
| `#introductions` | Say hi and tell us about yourself! What realms are you interested in? |
| `#showcase` | Share what you've built with OpenOctopus. Include a description and screenshots! |
| `#ideas` | Got an idea for OpenOctopus? Share it here. Upvote ideas you like with reactions |
| `#off-topic` | Non-project chat, memes, and random fun. Keep it friendly! |

### 🌍 REALMS

| Channel | Topic |
|---------|-------|
| `#realm-pet` | Pet realm — AI companions for your pets. Share setups, SOUL.md templates, and pet care automation |
| `#realm-family` | Family realm — AI agents for family coordination. Schedules, communication, care planning |
| `#realm-finance` | Finance realm — Personal finance agents. Budgets, investments, expense tracking automation |
| `#realm-work` | Work realm — Career and productivity agents. Task management, meeting prep, project coordination |

### ✨ SUMMON

| Channel | Topic |
|---------|-------|
| `#summon-showcase` | Show off your summoned entities! Share SOUL.md configs and how your AI companions behave |
| `#entity-design` | Discuss entity design patterns. How to write great SOUL.md files, personality tuning, and proactive rules |

### 🛠️ DEV

| Channel | Topic |
|---------|-------|
| `#dev-general` | General development discussion. Architecture, code questions, and technical decisions |
| `#tentacle-cli` | Tentacle CLI tool — installation, usage, commands, and troubleshooting |
| `#contributing` | How to contribute to OpenOctopus. PR workflow, good first issues, and contributor discussions |

### ❓ HELP

| Channel | Topic |
|---------|-------|
| `#setup-help` | Need help getting started? Ask here. Include your OS, version, and error messages |
| `#bug-reports` | Found a bug? Report it here with steps to reproduce. Check existing reports first |
| `#feature-requests` | Suggest new features or improvements. Use reactions to upvote requests you support |

### 🔊 VOICE

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
| @Reef Member | Default | — | Community members (default) |

### Role Permissions

| Permission | Octo Core | Tentacler | Realm Builder | Summoner | Reef Member |
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

1. Be respectful and constructive. No harassment, personal attacks, or discrimination.
2. Keep discussions on-topic. Use the appropriate channels. Off-topic chat goes in #off-topic.
3. No spam or unsolicited self-promotion. Share your projects in #showcase.
4. No unsolicited DMs. Don't DM other members without permission.
5. Search before asking. Check #setup-help and the docs before posting.
6. Use English in public channels.
7. Follow Discord's Terms of Service. No NSFW, illegal, or pirated content.

Enforcement: friendly reminder → formal warning → temporary timeout → ban.
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
