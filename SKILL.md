---
name: frontend-slop-guard
description: >-
  Mandatory UI-quality rules to read before any frontend work. Use before creating, editing,
  reviewing, or refactoring any visual interface, including HTML/CSS/JS/TS, React, Vue, Svelte,
  Astro, Tailwind, dashboards, landing pages, app screens, components, themes, and the visual
  styling of XAML, WPF, MAUI, React Native, or Flutter screens. Prevents the ten AI "slop UI"
  tells: gradient abuse, rainbow color vomit, pulsing and redundant status badges, fingernail
  card accent bars, emoji slop, misaligned elements, lazy default fonts (Inter, JetBrains Mono)
  with `//` gimmicks, chat-context redundant copy, overused glassmorphism and identical brutalism,
  and generic hype taglines. Load this for every frontend, UI, CSS, HTML, Tailwind, React, Vue,
  Svelte, dashboard, landing page, design, styling, component, theme, slop, or anti-slop task
  without exception.
---

# Frontend Slop Guard

This skill turns the ten AI "slop UI" tells from the source article "10 tells of a slop ui" (hereticpleb, September 27, 2026) into rules you can apply while writing and reviewing frontends.

## When to Read

- Read this every time you create or change a visual interface, without exception. This covers web frontends (HTML, CSS, SCSS, JS, TS, JSX, TSX, Vue, Svelte, Astro, Tailwind) and the visual styling of desktop and mobile screens (WinUI XAML, WPF, MAUI, React Native, Flutter).
- If the work touches screens, components, styles, themes, layouts, colors, typography, icons, cards, badges, or animations, load this skill first.
- When reviewing or refactoring an existing UI, use the same rules to find and remove slop tells.

## Core Principles

1. A UI is a functional tool. Do not style every screen like a landing page.
2. Every visual choice needs a reason. If you cannot explain a decoration in one sentence, do not add it.
3. Colors, gradients, animations, badges, and emoji are the exception, not the default. Start simple, then add only where it is needed.
4. At the end, ask "does this look like AI made it?" and if it does, remove the slop tells.
5. If the user provides an existing design system or brand guide, follow it. This skill corrects defaults; it does not override explicit direction.

## The Ten Slop Tells and Their Rules

Each section lists the tell, why it is slop, and the rule.

### 1. Gradients Everywhere

- Tell: Gradients on buttons, backgrounds, text, cards, and icons, often purple.
- Why it is slop: More gradients scatter attention and erase hierarchy. The source calls this the biggest and most noticeable tell.
- Rule: Use a gradient at most once per screen, on a single focal point. Default backgrounds, primary buttons, and body text to solid colors. Try a flat background with one accent color first.
- Self-check: If a screen has more than three gradients, remove them.

### 2. Rainbow Vomit

- Tell: Colors that do not go together, spread across the screen. Color is added just because there are many fields or items.
- Why it is slop: Color without meaning is noise, and it ignores the 70-30-10 rule.
- Rule: Follow 70-30-10. Keep about 70 percent neutral or dominant, 30 percent secondary, and 10 percent accent. Use color only to carry state or meaning. Separate items with spacing, dividers, and typographic hierarchy instead of color.
- Self-check: Explain each color's role in one sentence. Remove any color you cannot explain.

### 3. Pulsing and Redundant Status Badges

- Tell: "active", "verified", and "live" badges on everything, often with a pulsing dot. A badge shows a value that is always true.
- Why it is slop: If the value never flips, the badge carries no information. In the source, an "active" badge was never inactive because the app logs the user out instead, so the badge was meaningless. A "verified" badge means nothing without a verifier.
- Rule: Add a status badge only when the value actually changes. If it is always true, delete the badge and show the other state only when it occurs. Restrict pulsing animation to real-time state that truly needs the user's attention or action.
- Self-check: Ask whether the badge can ever be false. If it cannot, remove it.

### 4. Fingernail Cards

- Tell: A thin, rounded, colored accent bar on the left edge of a card, or a similar stripe on the top or corner.
- Why it is slop: Nearly every LLM puts this on every card, so it now signals slop instead of character. The source notes that no one ever consciously decided a card needed a fingernail.
- Rule: When a card needs emphasis, use background tone, borders, icons, or heading typography. Do not use the left fingernail accent bar as a default emphasis device.
- Self-check: Ask "would a fingernail improve this?". If the answer is no, leave it out.

### 5. Emoji Slop

- Tell: Emoji on headings, buttons, list items, and labels.
- Why it is slop: Emoji render differently across platforms, and using them as decoration looks unprofessional. The source says LLMs love emoji too much.
- Rule: When you need an icon, use one consistent icon set as SVG (for example Fluent, Lucide, or Heroicons). Use emoji only when the user entered it or the product identity genuinely needs it.
- Self-check: Check whether removing the emoji loses information. If it does not, replace it with an icon or remove it.

### 6. Misaligned Stuff

- Tell: SVG, ASCII art, icons, and list items that sit outside a box are almost always off their alignment. In the source's timetable example, the time labels and dots did not line up vertically.
- Why it is slop: Misalignment makes a screen look unfinished, and users lose trust without realizing why.
- Rule: Align every element to a grid or flex baseline. Put icons in fixed-size square boxes so their visual weight is consistent. Align irregular elements (SVG, artwork) explicitly inside their container.
- Self-check: Check the vertical and horizontal baselines, and fix anything that looks visually off.

### 7. Lazy Fonts and `//` Gimmicks

- Tell: No deliberate font choice, so it falls to Inter or system fonts. A programming-related site gets JetBrains Mono, and `//` appears wherever tech is mentioned.
- Why it is slop: Font choice sets the whole mood, so staying on the default makes the screen look like everywhere else. The `//` decoration is a cheap way to signal "technical".
- Rule: Choose a font deliberately to match the context and mood. Use a monospace font only for real code, numbers, and identifiers. Use `//` only in real code and comments, never as heading or label decoration.
- Self-check: Check whether the font distinguishes this screen, and whether every monospace and `//` has a functional reason.

### 8. Redundant Text Due to Chat Context

- Tell: Copy such as "Built with Hugo. Written from Neovim", "Built with Modern C++20 features", or "One campus. One app." that does not change any user decision. Details from the prompt leak straight into the UI.
- Why it is slop: The build tool, editor, and internal org details mean nothing to the user. The source says you can smell the prompt that produced the copy.
- Rule: Write only what helps the user decide what to do on the screen. Keep libraries, editors, dev environments, and internal consolidation details out of the UI. Use a slogan only when it is a real value proposition.
- Self-check: Ask whether removing the copy changes any user decision. If it does not, remove it.

### 9. Glassmorphism and Cookie-Cutter Brutalism

- Tell: Blurred glass as the default style with no exploration of other design languages. Brutalism that always uses the same colors and layout.
- Why it is slop: Glass only makes sense when layers overlap. Context-free glass and cloned brutalism read as templates, not character.
- Rule: Choose one design language deliberately to fit the project. Restrict glass to surfaces that genuinely overlap or float. If you use brutalism, vary color, typography, and layout to fit the project.
- Self-check: Check whether the design holds up without the effect. If it does, the effect is decoration, so reduce it.

### 10. Generic Taglines and Unnecessary Hype

- Tell: Words like "Elevate", "Seamless", "Next-Generation", "Supercharge", "Unleash", "Empower", and "Revolutionise". A grey subtitle automatically after every H1. Empty welcome copy such as "Welcome to your Dashboard, [Name]" on a tool screen.
- Why it is slop: Inflated copy adds no information and turns a tool into a landing page. A grey subtitle becomes a redundant restatement when it is added by habit.
- Rule: Do not use the banned words above or their variants. Add a subtitle under an H1 only when it supplies missing information. On tool screens, keep working labels and states, and drop welcome copy and marketing lines.
- Self-check: Check whether removing the subtitle or copy loses information. If it does not, remove it.

## Slop-Safe Defaults

- Start with flat backgrounds, and create depth with a subtle tone shift if needed.
- Pick one accent color and keep everything else neutral.
- Choose icons from a single set and keep their size and alignment consistent.
- Use animation only for changes the user needs to notice.
- Build typographic hierarchy from size, weight, and spacing, not color and decoration.
- Build components in their minimal reusable form, and treat special effects as exceptions.

## Pre-Ship Checklist

- [ ] The screen has three or fewer gradients, each with a reason.
- [ ] The palette follows 70-30-10.
- [ ] No status badge is always true, and no unnecessary pulsing animation remains.
- [ ] No fingernail accent bar sits on the left of a card.
- [ ] Emoji are used only for content purposes.
- [ ] Every element aligns to the grid and baselines.
- [ ] Fonts are chosen for the context, with no decorative `//`.
- [ ] No redundant copy or internal-detail copy remains.
- [ ] The design holds up without the glass effect and brutalism.
- [ ] No banned tagline words remain, and no grey subtitle is added by habit.

## Review Mode

When reviewing an existing UI, list the problems against the ten tells, and for each problem give the file, the location, and a concrete fix. Classify severity as "breaks function", "hurts trust", or "a matter of taste". Do not force taste issues; leave them as suggestions.

## References

- `references/source-10-tells-of-slop.md`: the original source article.
- `references/examples.md`: descriptions of the example images for each tell.
- `references/images/`: 16 example images for reference only.
