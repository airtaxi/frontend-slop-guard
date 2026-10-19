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
  and generic hype taglines, plus middle dot (·) separator abuse in UI copy, card overuse and
  icon tile stacks, colored glows and radial halos, ghost cards, eyebrow kickers and section
  numbers, decorative grid and stripe backgrounds, fake liveliness motion, decorative dashboard
  chrome, and shape-assembled SVG illustrations. Load this for every
  frontend, UI, CSS, HTML, Tailwind, React, Vue,
  Svelte, dashboard, landing page, design, styling, component, theme, slop, or anti-slop task
  without exception.
---

# Frontend Slop Guard

This skill turns the ten AI "slop UI" tells from the source article "10 tells of a slop ui" (hereticpleb, September 27, 2026) into rules you can apply while writing and reviewing frontends. It also adds tells that are not in the source article: middle dot separator abuse, and eight tells adapted from the anti-pattern rules of Impeccable (Paul Bakaus, Apache 2.0).

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

- Tell: Gradients on buttons, backgrounds, text, cards, and icons, often purple. Gradient text on headings and metrics. Purple-to-violet gradients, and cyan or neon ink on a dark background.
- Why it is slop: More gradients scatter attention and erase hierarchy. The source calls this the biggest and most noticeable tell. Purple and violet gradients and cyan on dark are the palette generated UIs converge on, so a gradient in those hues reads as slop on its own.
- Rule: Use a gradient at most once per screen, on a single focal point. Default backgrounds, primary buttons, and body text to solid colors. Try a flat background with one accent color first. Never fill text with a gradient; emphasize it with weight or size. Do not reach for purple, violet, or cyan-on-dark unless the brand actually owns those colors.
- Self-check: If a screen has more than three gradients, remove them. If any text uses `background-clip: text` with a gradient (or a gradient `Foreground` brush in XAML), make it solid.

### 2. Rainbow Vomit

- Tell: Colors that do not go together, spread across the screen. Color is added just because there are many fields or items.
- Why it is slop: Color without meaning is noise, and it ignores the 70-30-10 rule.
- Rule: Follow 70-30-10. Keep about 70 percent neutral or dominant, 30 percent secondary, and 10 percent accent. Use color only to carry state or meaning. Separate items with spacing, dividers, and typographic hierarchy instead of color.
- Self-check: Explain each color's role in one sentence. Remove any color you cannot explain.

### 3. Pulsing and Redundant Status Badges

- Tell: "active", "verified", and "live" badges on everything, often with a pulsing dot. A badge shows a value that is always true. The same status or label text repeated three or more times inside one card or panel.
- Why it is slop: If the value never flips, the badge carries no information. In the source, an "active" badge was never inactive because the app logs the user out instead, so the badge was meaningless. A "verified" badge means nothing without a verifier. Repeating the same text in several slots of one card is a template wired into every slot, not a message.
- Rule: Add a status badge only when the value actually changes. If it is always true, delete the badge and show the other state only when it occurs. Restrict pulsing animation to real-time state that truly needs the user's attention or action. Say a status once, in the slot where it matters most.
- Self-check: Ask whether the badge can ever be false. If it cannot, remove it. Check whether any text appears more than once in the same card.

### 4. Fingernail Cards

- Tell: A thin, rounded, colored accent bar on the left edge of a card, or a similar stripe on the top or corner. The same stripe on list items, callouts, and alerts. A thick accent border on a rounded card.
- Why it is slop: Nearly every LLM puts this on every card, so it now signals slop instead of character. The source notes that no one ever consciously decided a card needed a fingernail. A thick one-sided border also clashes with rounded corners.
- Rule: When a card needs emphasis, use background tone, borders, icons, or heading typography. Do not put a colored border thicker than 1px on only the left or right side of a card, list item, callout, or alert. Do not combine a thick accent border with a rounded corner radius.
- Self-check: Search for `border-left`, `border-right`, `border-inline-start`, and one-sided `BorderThickness` values (such as `4,0,0,0`) above 1px. Ask "would a fingernail improve this?". If the answer is no, leave it out.

### 5. Emoji Slop

- Tell: Emoji on headings, buttons, list items, and labels. Unicode symbols such as ★, ✓, →, and ⚡ standing in for icons.
- Why it is slop: Emoji render differently across platforms, and using them as decoration looks unprofessional. The source says LLMs love emoji too much. Unicode symbols take their shape and weight from whatever font renders them, so they never match a real icon set.
- Rule: When you need an icon, use one consistent icon set as SVG or an icon font (for example Fluent, Lucide, or Heroicons), with one stroke and weight. Use emoji only when the user entered it or the product identity genuinely needs it. Do not use Unicode symbols as icons.
- Self-check: Check whether removing the emoji or symbol loses information. If it does not, replace it with an icon or remove it.

### 6. Misaligned Stuff

- Tell: SVG, ASCII art, icons, and list items that sit outside a box are almost always off their alignment. In the source's timetable example, the time labels and dots did not line up vertically.
- Why it is slop: Misalignment makes a screen look unfinished, and users lose trust without realizing why.
- Rule: Align every element to a grid or flex baseline. Put icons in fixed-size square boxes so their visual weight is consistent. Align irregular elements (SVG, artwork) explicitly inside their container.
- Self-check: Check the vertical and horizontal baselines, and fix anything that looks visually off.

### 7. Lazy Fonts and `//` Gimmicks

- Tell: No deliberate font choice, so it falls to Inter or system fonts. The same handful of faces every generated UI converges on: Inter, Roboto, Geist, Plus Jakarta Sans, Space Grotesk, and Fraunces. An oversized italic serif (Fraunces, Recoleta, Playfair) as the hero headline. A programming-related site gets JetBrains Mono, and `//` appears wherever tech is mentioned.
- Why it is slop: Font choice sets the whole mood, so staying on the default makes the screen look like everywhere else. The oversized italic serif hero has become the default look of AI startup landing pages. The `//` decoration is a cheap way to signal "technical".
- Rule: Choose a font deliberately to match the context and mood. Set hero headlines in roman, or use a non-serif display face, unless the surface is genuinely editorial. Use a monospace font only for real code, numbers, and identifiers. Use `//` only in real code and comments, never as heading or label decoration.
- Exception: In native desktop and mobile apps, the platform's own UI font is the correct default (Segoe UI Variable on Windows, San Francisco on Apple platforms, Roboto on Android). The font rules above target web pages and branded surfaces, not native app chrome.
- Self-check: Check whether the font distinguishes this screen, and whether every monospace and `//` has a functional reason.

### 8. Redundant Text Due to Chat Context

- Tell: Copy such as "Built with Hugo. Written from Neovim", "Built with Modern C++20 features", or "One campus. One app." that does not change any user decision. Details from the prompt leak straight into the UI.
- Why it is slop: The build tool, editor, and internal org details mean nothing to the user. The source says you can smell the prompt that produced the copy.
- Rule: Write only what helps the user decide what to do on the screen. Keep libraries, editors, dev environments, and internal consolidation details out of the UI. Use a slogan only when it is a real value proposition.
- Self-check: Ask whether removing the copy changes any user decision. If it does not, remove it.

### 9. Glassmorphism and Cookie-Cutter Brutalism

- Tell: Blurred glass as the default style with no exploration of other design languages. Brutalism that always uses the same colors and layout. Hard offset shadows (`box-shadow: 4px 4px 0`) on a page that never committed to neobrutalism.
- Why it is slop: Glass only makes sense when layers overlap. Context-free glass and cloned brutalism read as templates, not character. A zero-blur block shadow is a costume, not a depth system.
- Rule: Choose one design language deliberately to fit the project. Restrict glass to surfaces that genuinely overlap or float. If you use brutalism, vary color, typography, and layout to fit the project. Use hard offset shadows only when the whole design is deliberately neobrutalist.
- Self-check: Check whether the design holds up without the effect. If it does, the effect is decoration, so reduce it.

### 10. Generic Taglines and Unnecessary Hype

- Tell: Words like "Elevate", "Seamless", "Next-Generation", "Supercharge", "Unleash", "Empower", "Revolutionise", "Streamline", "World-class", "Enterprise-grade", and "Cutting-edge". A grey subtitle automatically after every H1. Empty welcome copy such as "Welcome to your Dashboard, [Name]" on a tool screen. Sections that each land on a short rebuttal or a manufactured contrast ("Not a feature. A platform.", "No setup. Just results."). Dismissing something as "theater".
- Why it is slop: Inflated copy adds no information and turns a tool into a landing page. A grey subtitle becomes a redundant restatement when it is added by habit. One punchy contrast can be voice, but the same cadence repeated across sections is a generated rhythm.
- Rule: Do not use the banned words above or their variants. Pick a specific verb and noun that say what the product literally does. Add a subtitle under an H1 only when it supplies missing information. On tool screens, keep working labels and states, and drop welcome copy and marketing lines. Use a rebuttal or contrast line at most once per page. Say plainly what something does or does not do instead of calling it "theater".
- Self-check: Check whether removing the subtitle or copy loses information. If it does not, remove it. Count the "X. No Y." and "Not X. Y." lines; if there are more than one, rewrite the rest.

## Additional Tells

These tells are not in the source article. They follow the same format and carry the same weight as the ten above. Tells 12 to 19 are adapted from the anti-pattern rules of Impeccable.

### 11. Middle Dot Separators

- Tell: The middle dot `·` (U+00B7, `&middot;`) and its look-alikes (`•`, `∙`, `⋅`) used as an all-purpose separator. Metadata rows such as "5 min read · Design · Oct 2026", footers such as "Privacy · Terms · Contact", titles such as "Settings · Account", and Korean copy that lists items as "디자인·개발·운영".
- Why it is slop: LLMs reach for the middle dot whenever two pieces of text sit next to each other, so it now marks generated copy the same way the `//` gimmick does. It hides the relationship between the items (a list, a hierarchy, or a date and a category all look the same), it is hard to hit on small touch targets when it separates links, and screen readers either skip it or read it as "dot".
- Rule: Separate items with layout, not glyphs. Render each item as its own element and space them with `gap`, margins, or a thin divider drawn in CSS or XAML. Show hierarchy with breadcrumb chevrons or headings, and write lists in prose with commas or conjunctions (in Korean, use commas or "와/과", "및"). Use `·` only when the language's orthography requires it (for example Catalan "l·l") or when it appears in user-entered or brand content.
- Self-check: Search the changed files for `·`, `&middot;`, `&#183;`, `·`, and `•`. Replace every one that is not required by orthography or by content you were given.

### 12. Card Overuse and Icon Tiles

- Tell: Cards nested inside cards. A page built from a grid of same-size cards, each holding an icon, a heading, and a line of text. A small rounded-square tile holding an icon, stacked above every heading.
- Why it is slop: The card is the lazy container, and every generator outputs the icon, heading, and text card as its feature-section template. Nested cards add depth and borders without adding structure, and the icon tile is the most recognizable shape of that template.
- Rule: Never nest a card inside a card; flatten the hierarchy with spacing, typography, and dividers. Use a card only when the content is a distinct, self-contained object (an item the user can open, move, or act on). Vary the structure of feature sections: a list, a table, prose, or a single strong example often works better than a card grid. Put an icon beside its heading or let it sit in flow, without its own container.
- Self-check: Remove the card container and check whether the content still reads as grouped. If it does, the card was decoration. Check for any card whose parent is also a card.

### 13. Colored Glows and Radial Halos

- Tell: Zero-offset colored shadows that glow around buttons, cards, or text. Colored blurred shadows on a dark background. A saturated radial gradient fading to transparent behind a hero or section, like a spotlight or a floating colored cloud.
- Why it is slop: The glow is the default "cool" look of generated UIs. It imitates light without a light source, and the halo behind a hero competes with the copy it is supposed to support.
- Rule: Give shadows a vertical offset and a soft blur, and keep them neutral (a dark tint of the surface, not an accent color). Ground a dark surface with a solid color or a subtle tone shift instead of a halo. Reserve colored light for a deliberate material accent, not a background wash.
- Self-check: Search for `box-shadow` and `text-shadow` with a zero offset and a colored value, and for `radial-gradient` fading to `transparent` behind sections. In XAML, check `DropShadow` and `ThemeShadow` colors. Remove or neutralize each one that has no light source.

### 14. Ghost Cards

- Tell: Every card in a row wears both a 1px hairline border and a wide, diffuse shadow.
- Why it is slop: Border and shadow are two different ways to separate a surface. Using both on every card is a default nobody chose, and it is a recurring signature of generated UIs.
- Rule: Declare elevation once. Give a row of cards either a defined edge (a border or a tone shift) or a soft elevation (a shadow), not both. Reserve the combination for a single floating panel, such as a menu or a dialog, that genuinely sits above the page.
- Self-check: For each card style, check whether it sets both a border and a shadow. If it does, drop one.

### 15. Eyebrow Kickers and Section Numbers

- Tell: A tiny uppercase, letter-spaced label or pill chip sitting directly above a heading ("FEATURES", "WHY US", "NEW"). Small index labels such as "01", "02", and "03" beside each section heading.
- Why it is slop: The eyebrow above an oversized hero headline is now the default AI SaaS hero, and generated pages repeat it above every section. Numbered section labels are editorial scaffolding: the page numbers its own chapters instead of earning its structure.
- Rule: Let the heading carry its own weight; delete the eyebrow. If its words matter, work them into the heading or the body, or show them as a breadcrumb when they express real navigation. Number sections only when the sequence itself is information the reader needs, such as the steps of a procedure.
- Self-check: Look at the element directly above each heading. If it is a short uppercase label or a chip, remove it or merge it into the heading. Check whether removing each section number loses any information.

### 16. Decorative Backgrounds

- Tell: A grid or line field drawn with hairline gradient layers behind a hero or the whole page. Repeating diagonal or horizontal stripes used as surface texture. A warm cream or beige page background chosen by reflex as the "tasteful" default.
- Why it is slop: Grid and stripe overlays borrow the look of a blueprint or a canvas without anything to measure or draw on. The cream background has become the safe off-white that generated "tasteful" pages reach for, so it reads as a default rather than a palette.
- Rule: Keep backgrounds as plain surfaces. Use a grid overlay only on a real canvas, map, chart, blueprint, or measurement surface. Use texture only when it comes from the subject's own world. Pick the background color from the project's palette, not from habit.
- Self-check: Search for `repeating-linear-gradient` and for stacked `linear-gradient` layers with a fixed `background-size` cell. Ask whether the background color was chosen for this product or would fit any product.

### 17. Fake Liveliness Motion

- Tell: Bounce and elastic easing. Logos, testimonials, or features scrolling endlessly in a marquee. A blinking text cursor animated into a hero where nothing can be typed. The same fade-in or slide-up entrance on every section.
- Why it is slop: Each of these simulates activity instead of showing it. Bounce easing feels dated, a marquee demands attention it has not earned and hides half its content at any moment, a fake cursor borrows the dev-tool look as decoration, and an identical entrance on every section is motion nobody designed.
- Rule: Animate only changes the user needs to notice. Use a smooth ease-out (quart, quint, or exponential) instead of bounce or elastic curves. Show lists as static content the reader can move through at their own pace. Leave carets to real input fields. If a page gets an entrance animation, author one moment, and start from an already visible state so content never depends on the animation to appear.
- Self-check: Search for `cubic-bezier` values that overshoot (a control point outside 0 to 1), `bounce`, `elastic`, `marquee`, infinite `translateX` loops, and caret blink keyframes. In XAML, check for `BounceEase`, `ElasticEase`, and `RepeatBehavior="Forever"` on decorative elements. Check whether every section shares the same entrance.

### 18. Decorative Dashboard Chrome

- Tell: The hero metric template: a big number, a small label under it, a row of supporting stats, and an accent color. Sparklines, progress rings, and soft-shadowed rounded rectangles standing in for real content.
- Why it is slop: These shapes look like a dashboard without carrying a decision. A number with no comparison, no time frame, and no action is decoration, and a sparkline or ring with made-up data is a placeholder pretending to be content.
- Rule: Show a metric only when the user acts on it, and give it the context that makes it meaningful (a comparison, a period, or a target). Draw charts only from real data, at a size where they can be read. Never present illustrative numbers as if they were real; label sample data as sample data.
- Self-check: For each metric and chart, ask what the user would do differently after reading it. If the answer is nothing, remove it or replace it with the content it stands in for.

### 19. Shape-Assembled Illustrations

- Tell: A large inline SVG that builds a pictorial scene (a person, a laptop, a landscape, a rocket) out of a pile of circles, rectangles, and paths. Sketch-style SVG doodles and noise filters such as `feTurbulence` grain.
- Why it is slop: A scene assembled from primitives reads as placeholder clip art, not illustration. It is what a generator draws when it has no real artwork to use.
- Rule: Use real artwork, a photograph, or a deliberately drawn graphic for a hero-sized visual, or leave the space to the content. SVG stays first-class for geometry: icons, logos, diagrams, charts, and crisp vector shapes are fine. When an asset the user must provide is missing, leave a clearly marked slot instead of drawing a stand-in.
- Self-check: Check whether any SVG larger than an icon tries to depict a scene or an object. If it does, replace it with a real asset, a marked slot, or nothing.

## Slop-Safe Defaults

- Start with flat backgrounds, and create depth with a subtle tone shift if needed.
- Pick one accent color and keep everything else neutral.
- Choose icons from a single set and keep their size and alignment consistent.
- Use animation only for changes the user needs to notice.
- Build typographic hierarchy from size, weight, and spacing, not color and decoration.
- Build components in their minimal reusable form, and treat special effects as exceptions.
- Express elevation once per surface, with a neutral shadow that has an offset and a soft blur.

## Pre-Ship Checklist

- [ ] The screen has three or fewer gradients, each with a reason, and no text is filled with a gradient.
- [ ] The palette follows 70-30-10 and does not default to purple, violet, or cyan on dark.
- [ ] No status badge is always true, no unnecessary pulsing animation remains, and no card repeats the same text.
- [ ] No colored border thicker than 1px sits on only one side of a card, list item, callout, or alert.
- [ ] Emoji are used only for content purposes, and no Unicode symbol stands in for an icon.
- [ ] Every element aligns to the grid and baselines.
- [ ] Fonts are chosen for the context, with no decorative `//` (native app chrome keeps the platform font).
- [ ] No redundant copy or internal-detail copy remains.
- [ ] The design holds up without the glass effect and brutalism, and no hard offset shadow appears outside a neobrutalist design.
- [ ] No banned tagline words remain, no grey subtitle is added by habit, and no rebuttal cadence repeats.
- [ ] No middle dot (`·`) or bullet glyph is used as a decorative separator.
- [ ] No card is nested in a card, and no icon tile sits above a heading.
- [ ] No colored glow, zero-offset colored shadow, or radial halo remains.
- [ ] No card row wears both a hairline border and a wide shadow.
- [ ] No eyebrow label sits above a heading, and section numbers appear only for real sequences.
- [ ] No decorative grid or stripe background remains, and the background color comes from the palette.
- [ ] No bounce or elastic easing, marquee, fake cursor, or identical section entrance remains.
- [ ] Every metric and chart is real data the user acts on.
- [ ] No SVG assembled from primitive shapes stands in for an illustration.

## Review Mode

When reviewing an existing UI, list the problems against the nineteen tells, and for each problem give the file, the location, and a concrete fix. Classify severity as "breaks function", "hurts trust", or "a matter of taste". Do not force taste issues; leave them as suggestions.

## References

- `references/source-10-tells-of-slop.md`: the original source article.
- `references/source-impeccable.md`: the Impeccable anti-pattern rules that tells 12 to 19 and several additions to tells 1 to 10 are adapted from.
- `references/examples.md`: descriptions of the example images for each tell.
- `references/images/`: 16 example images for reference only.
