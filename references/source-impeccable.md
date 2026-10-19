# Source: Impeccable anti-pattern rules

- Project: Impeccable
- Author: Paul Bakaus
- URL: https://github.com/pbakaus/impeccable
- License: Apache License 2.0
- Files referenced: `crates/live/assets/antipatterns.json` (detector rule descriptions) and `skill/reference/craft-floor.md` (craft floor and refusals)

This table maps each Impeccable rule to the tell that covers it.

| Impeccable rule | Covered by |
| --- | --- |
| `gradient-text`, `ai-color-palette` | 1. Gradients Everywhere |
| `pulsing-dot`, `repeated-container-text` | 3. Pulsing and Redundant Status Badges |
| `side-tab`, `border-accent-on-rounded`, side-stripe border ban | 4. Fingernail Cards |
| Glyph and emoji icon ban | 5. Emoji Slop |
| `overused-font`, `italic-serif-display`, monospace as costume | 7. Lazy Fonts and `//` Gimmicks |
| Hard offset shadow ban, glassmorphism default ban | 9. Glassmorphism and Cookie-Cutter Brutalism |
| `marketing-buzzword`, `aphoristic-cadence`, `theater-slop-phrase` | 10. Generic Taglines and Unnecessary Hype |
| `nested-cards`, identical card grids, `icon-tile-stack` | 12. Card Overuse and Icon Tiles |
| `dark-glow`, `radial-halo`, `radial-spotlight-glow` | 13. Colored Glows and Radial Halos |
| `gpt-thin-border-wide-shadow` | 14. Ghost Cards |
| `hero-eyebrow-chip`, `kicker-above-heading`, `numbered-section-labels` | 15. Eyebrow Kickers and Section Numbers |
| `codex-grid-background`, `repeating-stripes-gradient`, `cream-palette` | 16. Decorative Backgrounds |
| `bounce-easing`, `marquee`, `blinking-cursor`, identical section entrances | 17. Fake Liveliness Motion |
| Hero metric template, decorative sparklines and rings | 18. Decorative Dashboard Chrome |
| `shape-assembled-illustration`, sketch-style SVG ban | 19. Shape-Assembled Illustrations |

Impeccable treats some of these as absolute bans (for example the eyebrow above a heading). This skill keeps its own severity model instead: Review Mode classifies each finding as "breaks function", "hurts trust", or "a matter of taste".
