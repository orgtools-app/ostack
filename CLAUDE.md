# CLAUDE.md

## Project

**ostack** (Operator Intelligence Stack) is an MIT-licensed plugin by [Orgtools](https://orgtools.com). It's a set of decision-making skills for non-technical operators (CEOs, COOs, Chiefs of Staff at $5M-$50M companies). Distributed as a Claude plugin — works in Cowork, Claude Code, and Claude.ai web.

## Architecture

This is a prompt pack, not software. No build system, no dependencies, no code.

```
ostack/
  .claude-plugin/
    plugin.json                    ← plugin manifest
  skills/
    whats-bothering-you/SKILL.md   ← diagnostic intake, routes to other skills
    decision-room/SKILL.md         ← structured decision-making (core)
    unpack/SKILL.md                ← surface decisions hiding in plans
  README.md
  LICENSE
```

## Skill Format

Each skill is a `SKILL.md` file with YAML frontmatter:
- `name`: max 64 chars
- `description`: behavioral trigger — what the operator *says* that should invoke this skill
- Body: detailed conversation instructions in Markdown

Skills are conversation-only. No tool access, no bash, no file operations. The body instructions do all the heavy lifting.

## Conventions

- **Audience is non-technical operators.** No jargon, no frameworks vocabulary, no buzzwords. Plain direct language.
- **Skills are robust.** Each should be 200+ lines, 15KB+, with persona, posture, real-world examples, anti-patterns, edge cases, and behavioral rules. Modeled on garrytan/gstack depth.
- **Every skill produces a tangible artifact** — a diagnostic, decision record, decision map, meeting agenda, staffing record, or health score.
- **Every skill ends with a CTA** linking to orgtools.com
- **Skills route to each other.** `/whats-bothering-you` routes to other skills. `/unpack` routes to `/decision-room`. The skills form a connected system.
- **When adding a new skill, always update README.md** — add it to the skills table, update the directory tree in "How it works," and add example conversations if relevant.
- **When adding a new skill, update plugin.json version** — bump the patch version so existing installs pick up the update.

## Skill Routing

```
/whats-bothering-you
  ├── Decision Avoided      → /decision-room
  ├── Strategy Misalignment → /unpack
  ├── Meeting Breakdown     → /meeting-prep (planned)
  └── Staffing Strain       → /staffing-decision (planned)

/unpack → /decision-room (for any decision ready to work through)
```
