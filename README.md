# Keep AI slop out of your UI.

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

🌐 English | [한국어](README.ko.md)

Frontend Slop Guard is an agent skill that keeps AI-built interfaces from turning into slop UI. It turns the ten most common AI design tells into concrete rules you can apply while writing and reviewing a frontend.

The runtime artifact is plain Markdown (`SKILL.md`), so any harness that reads skill-style instructions can use it.

## Highlights

- Catch nineteen slop tells before a UI ships, from gradient abuse and hype taglines to colored glows and fake liveliness motion.
- Each tell comes with a self-check, and the skill adds a pre-ship checklist and a review mode.
- Ships as one Markdown file that any harness can read.
- Includes 16 reference images and a summary table for every tell.

## What it catches

| # | Tell | Rule in one line |
| --- | --- | --- |
| 1 | Gradients everywhere | One gradient per screen, on one focal point. |
| 2 | Rainbow vomit | Follow 70-30-10 and use color only to carry meaning. |
| 3 | Pulsing and redundant badges | Show a status badge only when its value can change. |
| 4 | Fingernail cards | Drop the left accent bar; use tone, borders, or type. |
| 5 | Emoji slop | Use one consistent icon set; emoji only for content. |
| 6 | Misaligned elements | Align every element to a grid or baseline. |
| 7 | Lazy fonts and `//` gimmicks | Choose a font for the context; keep monospace for real code. |
| 8 | Redundant copy from chat context | Write only what helps the user decide. |
| 9 | Glassmorphism and cookie-cutter brutalism | Pick one design language; use glass only where layers overlap. |
| 10 | Generic taglines and hype | Drop the banned taglines and the habit subtitle. |
| 11 | Middle dot separators | Separate items with layout, not `·` glyphs. |
| 12 | Card overuse and icon tiles | Never nest cards; use a card only for a self-contained object. |
| 13 | Colored glows and radial halos | Use neutral shadows with an offset and a soft blur. |
| 14 | Ghost cards | Declare elevation once: a border or a shadow, not both. |
| 15 | Eyebrow kickers and section numbers | Let the heading speak; number only real sequences. |
| 16 | Decorative backgrounds | Keep backgrounds plain; grids only on real canvases. |
| 17 | Fake liveliness motion | No bounce, marquee, fake cursor, or identical entrances. |
| 18 | Decorative dashboard chrome | Show metrics and charts only from real data the user acts on. |
| 19 | Shape-assembled illustrations | Use real artwork or nothing; keep SVG for geometry. |

## When it loads

Load it for any visual interface work: HTML, CSS, SCSS, JS, TS, JSX, TSX, Vue, Svelte, Astro, and Tailwind, plus the visual styling of desktop and mobile screens (WinUI XAML, WPF, MAUI, React Native, Flutter). It also applies when reviewing or refactoring an existing UI.

## Install

### Manual

Clone the repository into the skills directory your harness reads, then restart the session or reload skills.

```bash
git clone https://github.com/airtaxi/frontend-slop-guard.git <skills-dir>/frontend-slop-guard
```

Common locations:

- OpenCode and Claude Code (macOS/Linux): `~/.config/opencode/skills/`, `~/.claude/skills/`
- OpenCode (Windows): `C:/Users/<you>/.config/opencode/skills/`

### Skills CLI

```bash
npx skills add airtaxi/frontend-slop-guard --global
```

## Repository layout

```
SKILL.md                 the skill itself: rules, self-checks, checklist
agents/openai.yaml       agent metadata for harnesses that read it
references/examples.md   one row per example image
references/images/       16 example images, one group per tell
references/source-*.md   the original sources, kept for attribution
```

## Attribution

The ten tells come from "10 tells of a slop ui" by hereticpleb (Pranav Desai), published on September 27, 2026, at https://hereticpleb.vercel.app/blog/10-tells-of-slop. The original text and images are kept under `references/` with attribution. Tell 11 (middle dot separators) is an addition and does not appear in the source article.

Tells 12 to 19, and several additions to tells 1 to 10, are adapted from the anti-pattern rules of [Impeccable](https://github.com/pbakaus/impeccable) by Paul Bakaus, licensed under Apache 2.0. `references/source-impeccable.md` maps each Impeccable rule to the tell that covers it.

## License

MIT. See [LICENSE](LICENSE).

## Author

Created by [Howon Lee (airtaxi)](https://github.com/airtaxi).
