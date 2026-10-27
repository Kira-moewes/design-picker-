# design-picker

A Claude skill for deciding a design by **seeing** instead of reading.

Claude first asks a few clickable questions (goal, audience, mood, dislikes), then walks you through
one design decision per round: every option is shown side by side as a mockup on your real content,
and you pick with one click. Every choice is logged, and at the end you get a locked design spec
(colours, fonts, spacing as ready-to-use tokens) plus a final mockup.

Works for websites, landing pages, software and dashboards, mobile apps, logos and brands,
presentations, print and social media graphics. Claude answers in your language.

## Install

**Claude Code**

```bash
git clone https://github.com/Kira-moewes/design-picker-.git
cp -r design-picker-/design-picker ~/.claude/skills/
```

Or with the skills CLI: `npx skills add https://github.com/Kira-moewes/design-picker-`

**claude.ai / Claude desktop app**

1. Download [`design-picker.zip`](design-picker.zip).
2. Settings → Capabilities → Skills → Upload skill, choose the zip.

## Use

Just say what you want, e.g. *"Help me pick a style for my website"*, *"show me design options"*,
*"gib mir Design-Vorschläge"*, or call it directly with `/design-picker`.

## License

MIT
