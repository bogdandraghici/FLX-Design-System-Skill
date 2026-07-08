# FlowX Design System Skill

Portable Claude skill for the FlowX design system. This folder mirrors the installed skill at `~/.claude/skills/flowx-design-system/` — `SKILL.md` plus reference files in both Markdown (human-readable) and JSON (machine-readable, authoritative) formats.

## Structure

```
SKILL.md           Skill entry point (rules, workflow, index)
references/
  foundations/     Foundation tokens
    colors         6 color palettes (blue, yellow, green, orange, red, neutrals) + semantic tokens + dark mode
    typography     Font families, sizes, weights, line heights, text presets
    spacing        20-step spacing scale (0-160px)
    elevation      5 shadow levels (xs-xl)
    radius         11-step border radius scale (2-120px)
    opacity        13-step opacity scale (0-90%)

  components/      Component specifications
    button         3 scopes (Brand, Danger, Success) x 3 variants x 4 states x 4 sizes
    checkbox       Selected/unselected/indeterminate x states (incl. hover) x 2 sizes
    radio          Selected/unselected x states (incl. hover, error, disabled) x 2 sizes
    input-field    5 states x 2 sizes, with prefix/suffix/icon slots
    select-field   4 states x 2 sizes, chip or text fill modes
    switch         On/off x 2 states x 2 sizes
    segmented-button  2 states x 2 sizes, 2-5 mutually exclusive segments
    tabs           Active/inactive x 2 sizes, with optional icon and counter
    dropdown-panel Multi-select/single x 2 sizes, search + nesting (site name: Tree)
    values-table   Tables: read-only/editing/error/warning, batch edit, bordered variant

  patterns/        Page-level patterns
    cards          Primary and Secondary cards, full-bleed table mode
    modals         4 widths, anatomy, button placement, multi-step
    typography-hierarchy  Text roles and section composition rules
```

## Conventions

- All colors reference the FlowX token scale (blue-500 = #006bd8)
- CSS variables use the `--flowx-` prefix
- Font family: Open Sans (primary), JetBrains Mono (monospace); icons: Phosphor Icons
- Both light and dark (inverted) mode values are included where applicable
- Last synced with the design system website: 2026-07-08
