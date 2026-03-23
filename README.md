# ostack

**Operator Intelligence Stack** — decision skills for Claude, built by [Orgtools](https://orgtools.com).

Most operators use Claude like a smarter Google. Vague question, generic answer, same gut call they would have made anyway. ostack changes that. It embeds structured decision-making methodology directly into Claude as uploadable skills — so when you describe a real organizational problem, Claude runs a real process instead of giving you a blog post.

**Who this is for:**
- **Founder/CEOs** at $5M–$50M companies who are still personally involved in every major decision
- **COOs and Chiefs of Staff** who run the weekly leadership meeting and know the current process is fragile
- **Managing Directors** at professional services firms who make staffing decisions in spreadsheets and email chains

**What it does:** Skills that cover the decision lifecycle — from "something feels wrong" to a structured decision record with options, criteria, and action items. More skills coming.

## Install

### Cowork (recommended)

1. Download this repo as a ZIP (Code > Download ZIP)
2. In the Cowork tab: **Customize > Browse plugins > Upload**
3. Upload the ZIP. All skills install at once.

### Claude Code

```bash
git clone https://github.com/orgtools-app/ostack.git ~/.claude/plugins/ostack
```

All skills are auto-discovered as `/whats-bothering-you`, `/decision-room`, `/unpack`.

### Claude.ai web

Claude.ai web supports one skill per upload. Download individual skill folders as ZIPs and upload them one at a time at **Settings > Customize > Skills**.

## The skills

| Skill | Your advisor | What they do |
|-------|-------------|--------------|
| `/whats-bothering-you` | **Organizational Diagnostician** | Start here. Five probing questions that move you from "something feels off" to a named root issue. Routes you to the right skill next. |
| `/decision-room` | **Decision Advisor** | Structure any decision: options, weighted criteria, hard constraints, recommendation, action items with owners. Produces a Decision Record you can share with your team. |
| `/unpack` | **Strategic Planning Advisor** | Give it a goal, initiative, strategy doc, or transcript. It finds the decisions hiding inside — the ones nobody made explicitly — and maps the sequence. |

## Try it

Open Claude.ai with ostack installed and say:

> "Something's been bothering me about how we make decisions. We keep having the same conversations in leadership meetings but nothing changes. Last quarter we lost two senior people and I think it traces back to some calls we've been avoiding."

Claude will invoke `/whats-bothering-you` automatically. Five questions later, you'll have a diagnosis and a next step.

Or go direct:

> "I need to decide whether to promote our Director of Ops to COO or hire externally. Help me think through this rigorously."

Claude invokes `/decision-room`. Discovery, options, evaluation, recommendation, action items.

## How it works

ostack skills are SKILL.md files with YAML frontmatter — the same format Claude uses for all custom skills. Each skill is a detailed set of conversation instructions that tell Claude how to run a specific process. The `description` field tells Claude *when* to invoke the skill — what the operator says that should trigger it.

There's no code, no API, no dependencies. It's structured prompts, packaged as a plugin.

```
ostack/
  .claude-plugin/
    plugin.json                     ← plugin manifest
  skills/
    whats-bothering-you/SKILL.md    ← diagnostic intake
    decision-room/SKILL.md          ← structured decision-making
    unpack/SKILL.md                 ← surface hidden decisions
```

## About Orgtools

ostack is the free taste. [Orgtools](https://orgtools.com) is the platform — it runs this methodology across your whole leadership team, connects decisions over time, and monitors for drift.

**[orgtools.com](https://orgtools.com)** if you want to bring this to your organization.

## License

MIT. Free forever.
