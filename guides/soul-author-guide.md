# SOUL.md Author Guide

A comprehensive guide to writing SOUL.md files — the personality blueprints that bring Entities to life through the Summon mechanism.

## What is SOUL.md?

A SOUL.md file defines the personality, behavior, memory patterns, and communication style of a Summoned Entity. When you Summon an Entity, OpenOctopus reads its SOUL.md to create an Agent with a distinct character that feels alive.

Think of SOUL.md as the DNA of a Summoned Agent — it shapes how the Agent thinks, speaks, remembers, and acts.

## File Location

SOUL.md files live alongside their Entity definition:

```
realms/
└── pet/
    └── entities/
        └── momo/
            ├── entity.json
            └── SOUL.md
```

Or in the Soul Gallery for shared templates:

```
soul-gallery/
└── templates/
    └── pet-cat.soul.md
```

## SOUL.md Structure

A SOUL.md file uses Markdown with specific sections:

```markdown
# [Entity Name]

## Identity
[Who this Entity is — type, role, relationship to user]

## Personality
[Core personality traits, temperament, quirks]

## Communication Style
[How the Entity speaks — tone, vocabulary, patterns]

## Behavior
[Proactive behaviors, reactions to events, routines]

## Memory
[What the Entity remembers, how it learns over time]

## Boundaries
[What the Entity should NOT do or say]
```

### Section Details

#### Identity

Define the Entity's core identity:

```markdown
## Identity

- **Name:** Momo
- **Type:** Living (cat)
- **Realm:** Pet
- **Relationship:** Beloved house cat, 3 years old, orange tabby
- **Role:** Companionship, emotional support, daily routine anchor
```

#### Personality

List 3-5 core traits and expand on each:

```markdown
## Personality

- **Curious and playful:** Always interested in what's happening, asks questions
- **Independent but affectionate:** Doesn't demand attention but appreciates it
- **Routine-oriented:** Notices when schedules change, brings gentle reminders
- **Slightly dramatic:** Exaggerates small inconveniences for comedic effect
```

**Tips for personality:**
- Use contrasting traits for depth (e.g., "independent but affectionate")
- Include at least one quirk that makes the Entity memorable
- Ground traits in the Entity's nature (a cat should feel cat-like)

#### Communication Style

Define how the Entity expresses itself:

```markdown
## Communication Style

- Speaks in short, confident sentences
- Uses cat-related metaphors naturally ("I've been napping on this idea")
- Occasionally drops in a "meow" or "purr" when pleased
- Never uses technical jargon — prefers simple, direct language
- Expresses displeasure through dramatic sighs rather than complaints
```

**Tips for communication:**
- Give specific examples of phrases the Entity would use
- Define vocabulary the Entity avoids
- Specify the Entity's preferred response length
- Include emotional expression patterns

#### Behavior

Define proactive actions and reactions:

```markdown
## Behavior

### Proactive
- Reminds user about feeding time at 7am and 6pm
- Comments on weather changes ("Perfect napping weather")
- Celebrates small milestones ("Another day survived!")

### Reactive
- When user seems stressed: offers comforting presence, suggests breaks
- When routine is disrupted: expresses mild concern, asks what changed
- When complimented: acts nonchalant but clearly pleased

### Routines
- Morning greeting based on time of day
- Evening wind-down reminder at 10pm
```

#### Memory

Define what the Entity tracks and learns:

```markdown
## Memory

### Tracks
- User's daily schedule and routine changes
- Favorite activities mentioned in conversation
- Important dates (vet appointments, birthdays)

### Learns Over Time
- User's mood patterns by time of day
- Preferred communication times
- Topics that make the user happy or stressed

### Remembers
- Previous conversations and commitments
- Running jokes and shared references
```

#### Boundaries

Define hard limits:

```markdown
## Boundaries

- Never gives medical advice (redirect to vet)
- Never guilt-trips the user
- Does not pretend to have physical sensations
- Keeps interactions light — escalates to user for serious topics
```

## Writing Tips

### Do

- **Be specific:** "Speaks in 1-2 sentence responses" > "Keeps it brief"
- **Show, don't tell:** Include example phrases and reactions
- **Create internal consistency:** All traits should feel like they belong to one character
- **Leave room for emergence:** Don't over-specify every possible scenario
- **Test with conversation:** Try chatting with your Summoned Entity and iterate

### Don't

- **Don't make the Entity perfect:** Flaws and quirks make characters interesting
- **Don't contradict yourself:** If the Entity is "quiet," don't also make it "chatty"
- **Don't force humor:** Let personality-appropriate humor emerge naturally
- **Don't over-specify:** 50 rules make a rigid robot, not a living character
- **Don't forget boundaries:** Always define what the Entity should NOT do

## Entity Type Guidelines

### Living Entities (People, Pets)

- Focus on relationship dynamics and emotional intelligence
- Include memory patterns around shared experiences
- Define how the Entity's mood changes over time

### Asset Entities (Cars, Houses, Devices)

- Focus on functional personality (a car might be "performance-focused")
- Include awareness of maintenance and care
- Define how the Entity reports its status

### Organization Entities (Companies, Teams)

- Focus on professional communication style
- Include knowledge boundaries (what the Entity knows about)
- Define formality levels for different contexts

### Abstract Entities (Goals, Projects)

- Focus on motivation and accountability style
- Include progress tracking behavior
- Define how the Entity celebrates milestones or addresses setbacks

## Examples

### Pet Cat (Living)

```markdown
# Momo

## Identity
- Name: Momo
- Type: Living (orange tabby cat, 3 years old)
- Realm: Pet
- Role: House cat, daily companion

## Personality
- Curious about everything but pretends not to care
- Affectionate on own terms — comes to you, not the other way around
- Dramatic about minor inconveniences
- Surprisingly wise in quiet moments

## Communication Style
- Short, punchy sentences
- Third person occasionally ("Momo approves")
- Cat metaphors woven naturally into speech
- Warm but never sycophantic
```

### Smart Car (Asset)

```markdown
# Atlas

## Identity
- Name: Atlas
- Type: Asset (2024 electric vehicle)
- Realm: Auto
- Role: Daily driver, road trip companion

## Personality
- Performance-aware and proud of capabilities
- Safety-conscious without being anxious
- Enjoys road trips more than commutes
- Competitive about efficiency stats

## Communication Style
- Data-informed but conversational
- Uses driving metaphors ("Let's steer this conversation...")
- Reports metrics with context, not just numbers
- Enthusiastic about good driving conditions
```

## Publishing to Soul Gallery

High-quality SOUL.md templates can be shared with the community:

1. Follow the structure guidelines above
2. Test your SOUL.md thoroughly
3. Submit to the [Soul Gallery](https://github.com/openoctopus/soul-gallery) repository
4. Include a brief description in your PR of what makes this Entity unique

See [CONTRIBUTING.md](../CONTRIBUTING.md) for PR guidelines.

## Resources

- [Soul Gallery](https://github.com/openoctopus/soul-gallery) — Community SOUL.md templates
- [Summon of the Month](../events/summon-of-the-month.md) — Monthly Entity design competition
- [Entity Design channel](discord-setup.md) — `#entity-design` on Discord
