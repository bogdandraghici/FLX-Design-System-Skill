---
name: flowx-design-system
description: Use when the user asks to build, style, or update any UI or design prototype using the FlowX Design System (FlowX DS, FlowX tokens, FlowX components), or to check, audit, or review existing pages/prototypes for compliance with FlowX styles and components. Supplies authoritative tokens for colors, typography, spacing, elevation, radius, and opacity, component specs for button, checkbox, radio, input-field, select-field, switch, segmented-button, tabs, dropdown-panel (tree), and values-table, plus pattern specs for cards, modals, typographic hierarchy, and empty states. Triggers on explicit mentions like "FlowX", "FlowX Design System", "FlowX DS", references to the FlowX component library, or requests like "does this follow the design system". Do NOT activate for generic UI work that doesn't mention FlowX.
---

# FlowX Design System

Authoritative specs for FlowX foundations and components. Every UI produced under this skill **must** use these tokens and component specs exactly — never guess colors, spacing, radii, or type.

## Core rules

1. **JSON is authoritative.** Always read the relevant `references/**/*.json` file before producing styled output. The `.md` twins are human reference only — do not rely on them for exact values.
2. **Framework-agnostic output.** Do not assume React, Tailwind, Vue, or any stack. Emit whatever the user's context calls for (plain HTML/CSS, React + CSS, Svelte, etc.). Default to plain HTML/CSS with CSS custom properties if no framework is specified.
3. **Tokens, not raw values (when possible).** If the target framework supports CSS variables, expose tokens as `--flowx-*` custom properties (e.g., `--flowx-color-blue-500: #006bd8`) and reference them. When the target can't use variables, inline the hex/px values read from the JSON — never approximate.
4. **Light mode is the default.** Only use the `inverted`/dark values from the JSON when the user asks for dark mode, inverted surfaces, or a dark-background context.
5. **Use library components first.** If a needed UI element exists in `references/components/`, implement it exactly per its JSON spec (sizes, states, paddings, colors, radii, typography).
6. **Patterns govern page structure.** Cards, modals, and text hierarchy have their own specs in `references/patterns/` — use them whenever a prototype has a page layout, a dialog, or headings/body text (which is almost always).
7. **Compose, don't invent.** For UI with no component or pattern spec (nav, toasts, breadcrumbs, tables other than values-table, etc.):
   - Compose from library primitives where possible (e.g., a form row = FlowX input-field + label; a toast's action = a FlowX tertiary button).
   - Style the surrounding container using foundation tokens only — FlowX colors, spacing scale, radius scale, elevation levels, typography presets.
   - Never import or style with an external design language (Material, Bootstrap, shadcn defaults, etc.).
8. **Open Sans** is the primary typeface; **JetBrains Mono** is the only monospace. Always set one of these when emitting text styles. For UI icons, use Phosphor Icons (the FlowX icon library) — do not mix in other icon sets.

## Workflow for any UI request

1. **Identify** which FlowX patterns, components, and foundations are needed.
2. **Read** the relevant JSON files with the Read tool (do NOT read the `.md` twins unless the JSON is ambiguous):
   - Foundations: always read the JSON for every token category you'll touch (colors, spacing, radius, typography, elevation, opacity).
   - Patterns: read `cards.json` and `typography-hierarchy.json` for any full page/screen; `modals.json` for any dialog.
   - Components: read the JSON for every library component you'll use.
3. **Produce** the UI, referencing exact token names/values. When choosing a color role, prefer semantic tokens (from `colors.json` → `semantic`) over raw palette steps when one fits.
4. **Verify** before finishing: every color, spacing value, radius, shadow, and font size you emitted can be traced back to a token or spec in the files you read.

## Index

Paths are relative to this SKILL.md.

### Foundations (`references/foundations/`)
- `colors.json` — 6 palettes (blue, yellow, green, orange, red, neutrals) × 10 steps, semantic tokens, dark-mode overrides
- `typography.json` — Open Sans + JetBrains Mono, sizes, weights, line-heights, text presets
- `spacing.json` — 20-step scale (0–160px)
- `radius.json` — 11-step scale (2–120px)
- `elevation.json` — 5 shadow levels (xs–xl)
- `opacity.json` — 13-step scale (0–90%)

### Components (`references/components/`)
- `button.json` — scope (Brand/Danger/Success) × variant (Primary/Secondary/Tertiary) × state × 4 sizes (Medium/Small/XS/XXS), light + inverted
- `input-field.json` — 5 states × 2 sizes, prefix/suffix/icon slots
- `select-field.json` — 4 states × 2 sizes, chip multi-select
- `checkbox.json` — selected/unselected × 3 states × 2 sizes, border + subtitle options
- `radio.json` — selected/unselected × 3 states × 2 sizes, border + subtitle options
- `switch.json` — on/off × 2 states × 2 sizes
- `segmented-button.json` — 2 states × 2 sizes, 2–5 mutually exclusive segments
- `tabs.json` — active/inactive × 2 sizes, optional icon + counter
- `dropdown-panel.json` — multi-select/single × 2 sizes, search + nesting (called "Tree" in some site URLs)
- `values-table.json` — tables (renamed from "Values Table" to "Tables" on the site): read-only/editing/error/warning states, inline editing with validation, batch edit, bordered standalone variant

### Patterns (`references/patterns/`)
- `cards.json` — Primary cards (white surface + shadow on the grey app background, structure a page) and Secondary cards (bordered, group content inside a Primary, sizes L/M/S), full-bleed table mode, in-card typography
- `modals.json` — 4 widths (XS 400 / S 600 / M 800 / L 80% screen), header/content/footer anatomy, button placement rules, multi-step behavior, light + dark
- `typography-hierarchy.json` — named text roles (Page Title, Section Title, Subsection Title, Description), spacing between levels, section-card composition rules
- `empty-states.json` — the no-content model: centered stack of a 24px icon, bold title, caption, and optional secondary-button CTA, optionally in a bordered container; Medium (full) vs Small (subtitle only) sizes

If the user asks for something not in this index (nav bar, toast, tooltip, accordion, stepper, breadcrumb, etc.), fall back to rule 7: **compose from primitives + foundation tokens**.

## Building a screen or prototype

For any full page or screen, start from the patterns, not the components:
1. App background is neutrals-50 (`#f7f8f9`); structure the page with **Primary cards** and group content inside them with **Secondary cards** (`patterns/cards.json`).
2. Set headings and body text from the **typography hierarchy** roles (`patterns/typography-hierarchy.json`) — never improvise font sizes.
3. Dialogs follow `patterns/modals.json`, including its button placement rules.
4. When a section or page has no content yet, use the **empty state** model (`patterns/empty-states.json`) centered inside its card.
5. Fill in the interactive elements from `references/components/`.

## Auditing an existing prototype

Use this mode when the user asks to check, review, or audit pages they've already built against the design system.

1. **Inventory the styling.** Grep the prototype's source for every concrete style decision:
   - colors: `#[0-9a-fA-F]{3,8}`, `rgb(`, `rgba(`, `hsl(`, and named CSS colors, plus Tailwind color classes (`bg-blue-500`, `text-gray-*`) if Tailwind is used
   - typography: `font-family`, `font-size`, `font-weight`, `line-height` (and text-size classes), `@font-face` / font `@import`s
   - geometry: `border-radius`, `padding`, `margin`, `gap`, `box-shadow`, `opacity`
   - icons: icon-font class names (`material-icons`, `fa-`, `bi-`, ...), icon library imports, inline `<svg>` provenance — anything that isn't Phosphor
2. **Build the allowed sets** by reading the foundation JSONs: every palette + semantic hex from `colors.json`, the size/weight/line-height combos from `typography.json`, the step values from `spacing.json`, `radius.json`, `opacity.json`, and the shadows from `elevation.json`. A value is compliant only if it appears there or in a component/pattern JSON being used — component and pattern specs legitimately contain values that are not foundation tokens (e.g. the Primary card shadow `2px 2px 24px rgba(22,52,98,.08)` is correct despite not being an elevation level).
3. **Check the components.** For each UI element that has a spec (buttons, inputs, checkboxes, tabs, modals, cards, ...), compare the implementation against its JSON: fills, strokes, text colors per state, paddings, heights, radii, font sizes/weights. A required property that is **absent** (a button missing its spec line-height, a card missing its shadow) counts the same as a wrong value. Also check structure: page background neutrals-50, Primary/Secondary card usage, typography hierarchy roles, modal button placement, Open Sans / JetBrains Mono only, Phosphor icons only.
4. **Report, don't fix.** Produce a findings list grouped by file. Category order is severity order, and one finding = one root cause (a disabled button with two wrong colors is one finding; a foreign font on `body` is one finding even though every child inherits it):
   - **Violation** — contradicts a spec that governs this element: wrong or missing value for a spec'd component/pattern/role, foreign font or icon set, Tailwind/Material default colors. Quote the file:line, the found value, and the correct token/value with its source reference file.
   - **Off-system** — no specific spec governs the element, and the value is off the foundation scales (in-between spacing, custom shadow on a bespoke element). Suggest the nearest token.
   - **Compliant-but-fragile** — correct values hardcoded where a `--flowx-*` variable is available.
   Summarize with a count per category and per file. Only apply fixes when the user asks; then fix per the same JSONs.

Judgment calls: near-miss colors (like `#006bd7` vs blue-500 `#006bd8`) are violations, not coincidences — flag them as typos. Dark-mode values appearing on light surfaces are violations even though the hex exists in the JSON. Do not flag content colors inside images/illustrations or third-party embeds.

## Common pitfalls to avoid

- Emitting UI without reading the JSON first → uses wrong colors/paddings.
- Applying a component size, state, or variant that isn't defined in its JSON.
- Using Tailwind default colors/spacing instead of FlowX tokens when Tailwind is the target (configure Tailwind with FlowX tokens instead).
- Rounding or "tidying" spacing/radius values — the scale is authoritative.
- Picking a raw palette step when a semantic token exists for that role.
- Using dark-mode values on a light background (or vice versa).
