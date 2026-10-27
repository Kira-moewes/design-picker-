---
name: design-picker
description: >-
  Visual design interview: first a short round of clickable questions about goal, audience, mood
  and dislikes, then one design decision per round with every option shown side by side as a
  visual mockup on the user's real content and a one-click "take this" button, decisions logged
  to a file, ending in a locked design spec (tokens + composite mockup) ready to implement. Works
  for any design work: website, landing page, web or desktop software, mobile app, dashboard,
  logo and brand, presentation, print, social media graphics. Use whenever the user wants to work
  out a look, style, design system, colours, fonts, layout or UI direction and wants to see
  options before deciding, e.g. "gib mir Design-Vorschläge", "zeig mir visuelle Beispiele",
  "lass uns das Design zusammen festlegen", "ich weiß noch nicht wie es aussehen soll",
  "show me options", "help me pick a style", and also when the user keeps answering text
  questions with "zeig mir das".
---

# Design picker

A design interview where the user decides by *seeing*, not by reading descriptions.
People who are not designers cannot judge "phosphor green vs. cyan" or "airy vs. compact"
from words; they judge instantly from a picture. So after a short opening round of questions,
every question comes with a visual, and the user's answer is one click.

The method came out of a real session: text-only design questions got the reply "gib mir für
alles visuelle Beispiele". After switching to visuals, every decision took one message.

## Language and tone

- Talk in the user's language (German user: German labels, buttons, log). Button text in the
  user's language too ("Nehmen ↗" in German, "Take this ↗" in English).
- The user may be a layperson: no design jargon without a plain explanation in brackets
  ("Kontrast (wie gut sich Schrift vom Hintergrund abhebt)").
- Keep prose around each visual to 1–2 sentences. The visual is the question.

## The loop

0. **Ask what they want first.** One short round of 3–4 questions in a single message, each
   with clickable answers and always a free-text option. Skip what the conversation already
   answered; skip the round entirely if everything is known.
   - **What is it:** website, app, software, logo, presentation … (only if unclear)
   - **Goal:** what the design should achieve (look trustworthy, feel fast, stand out, sell …)
   - **Audience:** who uses or sees it (age, expertise, context such as phone at the pool)
   - **Mood:** 4–6 mood words to pick several from (ruhig, sportlich, verspielt, edel,
     technisch, warm …)
   - **Dislikes and must-haves:** what bothers them today, what they never want, fixed
     brand colours or logo, references they like (links welcome)
   Log the answers as the first rows of the decision log.
1. **Get real content.** Mockups use the user's actual names, texts, menu items, numbers. Take
   them from the project files or the conversation; if there are none, ask once for 3–5 real
   examples (headline, a few menu items, one typical data row). Never use lorem ipsum: it makes
   every option look alike.
2. **Frame the brief.** In 3–5 lines restate what is being designed, for whom, the step 0
   answers and every decision already made. If there is no direction yet, the first visual
   round is 3 whole-look directions (see "Directions").
3. **Plan the decision list** privately: the 6–10 decisions that change the result most,
   biggest first (see "Decision lists by type"). Skip what is decided. Tell the user roughly how
   many rounds ("Frage 3 von etwa 8") so it feels finite.
4. **One decision per round.**
   - One visual with 3–4 options (up to ~12 swatches for colour), all on the same real content.
   - Everything already decided stays fixed in every option; only this decision varies.
   - Under each option one short line: what it feels like and its trade-off.
   - Each option has a "take this" button that sends the choice back as a message. For colour,
     a live picker: clicking a swatch recolours one larger mockup, plus one "take this" button.
   - Name your recommendation in the prose with a one-line reason; do not favour it visually.
5. **Log the decision immediately** and confirm it in one line ("Notiert: Mint (#5eead4).")
   before the next round.
6. **Follow the user, not the plan.** A question back: answer with a visual. "Zeig mehr":
   widen the options. A changed earlier answer: update the log and rebuild later rounds on it.
   A new request in between: handle it, then resume where the interview stopped.
7. **Finish with the spec.** One composite mockup with every decision applied (the key screen
   or page; light and dark if relevant; desktop and phone width for web/app), plus the token
   table (see "Final spec"). Ask: build it now, adjust something, or hand it over.

## Decision lists by type

Pick the list that fits, merge lists for mixed work, drop what is irrelevant.

- **Website / landing page:** direction → hero layout (image, text, video) → typography →
  accent colour → background and colour mode → navigation style → section rhythm and whitespace
  → buttons and links → imagery style (photo, illustration, none) → motion → footer.
- **Software / web app / dashboard:** direction → typography → accent colour → background and
  colour mode (light, dark, both) → density (compact vs airy) → navigation (sidebar, top bar,
  tabs) → tables and lists → forms and controls (inputs, checkboxes, radius) → charts and data
  colours → empty states and feedback (toasts, errors) → motion.
- **Mobile app:** direction → typography → accent colour → colour mode → tab bar vs menu →
  card vs list style → touch target size and spacing → icons → motion and transitions.
- **Logo / brand:** wordmark vs symbol vs both → letterform style (geometric, humanist, serif,
  hand) → symbol idea (3–4 concepts) → colour → lockups (horizontal, stacked, icon only) →
  small-size check (favicon, app icon).
- **Presentation / print / social:** direction → typography → colour → layout grid → image
  treatment → data visualisation style → title slide / cover.

## Directions (when there is no direction yet)

Show 3 clearly different whole looks on the same excerpt, each with a name and a two-line
character sketch. Make them genuinely different (e.g. technical / editorial / playful), not
three shades of one safe look. Avoid the generic AI look unless the brand calls for it:
indigo or violet accents, dark mode without a reason, cards around everything, emoji as icons,
decorative coloured side stripes, purple-to-blue gradients, cream background with serif
"calm editorial".

## Building the visuals

Use the best tool the environment offers, in this order:
1. An inline visual or widget tool (e.g. `show_widget`; read its instructions once first).
   Buttons call its send-message function (e.g. `sendPrompt('Akzentfarbe: Mint')`).
2. An Artifact or published HTML page, if available.
3. A local HTML file opened in a browser or preview pane.
4. No rendering at all: describe options with exact values and ask the user to reply with the
   option letter. Say once that visuals are not available here.
Where buttons cannot send messages, label options A/B/C/D and ask for the letter.

Rules for every visual:
- Render the mockup's own colours explicitly (it *is* the design being judged); use the host's
  theme only for the surrounding labels and buttons.
- Load fonts that are being compared (e.g. Google Fonts) so the real typeface shows.
- Show motion live when motion is the decision, not as a description.
- Compact: options side by side in a responsive grid, ~250–300 px tall each; stacks on phones.
- Check contrast: body text at least 4.5:1, large text and controls 3:1 (WCAG AA). If an option
  needs an adjusted value to pass (e.g. a darker accent for light mode), show the adjusted one.

## Decision log

Keep `design-decisions.md` in the project folder (or the scratchpad / a temp folder if there is
no project). Update it after every answer so decisions survive a context reset and can be handed
to another person or agent verbatim:

```markdown
# Design decisions – <product>
| # | Decision | Choice | Value / token | Why (user's words if given) |
|---|----------|--------|---------------|-----------------------------|
| 0 | Goal | vertrauenswürdig, sportlich | — | Fragerunde |
| 1 | Direction | Technisch | — | "A am besten" |
| 2 | Accent | Mint | #5eead4 (light mode: #0f9488) | gefiel am besten |
Open: <decisions still to come>
```

## Final spec

Deliver in the log file and in the reply:
- **Tokens:** colours (background, surface, text, muted text, border, accent, success, warning,
  danger; light and dark values), font families and sizes (scale), font weights, spacing scale,
  corner radius, shadows (or "none"), motion durations.
- **Ready-to-use form** for the project's stack: CSS custom properties by default; a Tailwind
  config, design-token JSON or brand sheet when that fits better.
- **Composite mockup** of the key screen with everything applied.
- **Do and don't list** (5–8 lines) so later work stays consistent.

## Rules of thumb

- After step 0, never ask a text-only design question; every later question comes with a visual.
- One decision per round; never bundle two visual choices into one picture.
- Do not change the product while grilling. Building starts only after the user approves the
  final spec, or when they explicitly ask to build earlier.
- Respect fixed constraints from step 0 (brand colours, logo, accessibility needs) in every option.
- When an option needs a technical adjustment to work, show it rather than mention it.
