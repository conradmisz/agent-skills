# UI Context

<!-- Keep under ~100 lines when filled. -->

## Theme

[One paragraph: the visual language and the hard rule that gates new
elements — e.g. "a physical instrument panel; anything that would not
exist on real hardware gets redesigned".]

## Colors

| Role            | CSS Variable     | Value    |
| --------------- | ---------------- | -------- |
| Page background | `--bg`           | `#[hex]` |
| Surface         | `--surface`      | `#[hex]` |
| Primary text    | `--ink`          | `#[hex]` |
| Muted text      | `--ink-2`        | `#[hex]` |
| Accent          | `--acc`          | `#[hex]` |
| Readout text    | `--readout`      | `#[hex]` |
| Attention       | `--attn`         | `#[hex]` |
| Success         | `--ok`           | `#[hex]` |

## Typography

| Role      | Font         | Variable  |
| --------- | ------------ | --------- |
| UI text   | [font]       | `--sans`  |
| Code/mono | [font]       | `--mono`  |
| Readouts  | [font]       | `--read`  |

## Border Radius

| Context           | Radius |
| ----------------- | ------ |
| Controls          | [px]   |
| Panels            | [px]   |
| Overlays          | [px]   |

## Component Library

None. Hand-written CSS components in the single UI file: [list the
class names and what each is]. [Library] is the only UI dependency.

## Layout Patterns

- [Columns and fixed widths]
- [Row structure of the main area]
- [How overlays appear and close]
- [Display/size vocabulary — e.g. "two display sizes only"]

## Icons

[e.g. Inline SVG only, drawn to match the theme. No icon font.]
