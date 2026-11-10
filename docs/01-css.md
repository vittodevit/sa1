# 01 — CSS guide and complete class reference

This file explains the project's CSS files and documents every reusable class
in them.

The project is desktop-first. The layout has a few `min-width` breakpoints for
the article sidebar and the footer. There is no mobile navigation.

## Files and load order

The project uses two stylesheets:

- `styles/styles.css` contains the design tokens, base element styles,
  typography and the three global utilities.
- `styles/shared.css` contains layout primitives and reusable components.

Always load them in this order:

```html
<link rel="stylesheet" href="styles/styles.css">
<link rel="stylesheet" href="styles/shared.css">
```

`components.html` also has a local `<style>` block for the gallery previews.
Those classes are not loaded by `article.html` and are not part of the shared
component system.

## How to read a class name

The project uses the BEM pattern:

- `.card` is the main block.
- `.card__title` is a part inside that block.
- `.btn--primary` is a variation of that block.

Classes can be combined. For example, `class="grid grid--3"` means “use the
basic grid and choose the auto-fitting three-column version”. A state or a
utility can also be added when it has a clear, single purpose.

Layout and utility classes are intentionally outside BEM: `.container`,
`.grid`, `.stack`, `.cluster`, `.surface`, `.visually-hidden`, `.text-sm` and
`.text-muted` are small primitives, not components.

## Design tokens

Avoid raw values in new components. Use the variables declared in
`styles/styles.css`.

### Core palette

| Token | Value | Role |
| --- | --- | --- |
| `--yale-blue` | `#133c55` | One of the five brief colours, used as a surface tone. |
| `--cornflower-ocean` | `#386fa4` | Mid blue in the family. |
| `--fresh-sky` | `#59a5d8` | Brighter blue. |
| `--frozen-lake` | `#84d2f6` | Light blue. |
| `--frosted-blue` | `#91e5f6` | The main accent in the `brand` theme. |

The `--blue-1000` … `--blue-100` scale is derived from those five colours. It
runs from almost black (`--blue-1000`) to almost white (`--blue-100`) and keeps
the interface in one blue family. The darkest steps are used for backgrounds
and surfaces; the lightest steps are used for accents and text.

The neutral text tones are `--slate-100` (`#f4f6f9`), `--slate-300`
(`#dbe3f2`) and `--slate-400` (`#c5cbe8`).

### Semantic colours

Components refer to semantic names, not to the raw palette:

| Token | Role |
| --- | --- |
| `--color-bg` | Page background. |
| `--color-bg-deep` | Deeper background, used by the footer. |
| `--color-surface` | Default panel surface. |
| `--color-surface-2` | Slightly raised surface. |
| `--color-surface-3` | Card surface. |
| `--color-surface-4` | Highest surface step. |
| `--color-text` | Main text. |
| `--color-text-muted` | Secondary text. |
| `--color-text-dim` | Metadata and de-emphasised text. |
| `--color-border` | Default border. |
| `--color-border-strong` | Stronger border. |
| `--color-accent` | Main accent colour. |
| `--color-accent-strong` | Stronger accent for hover and emphasis. |
| `--color-accent-text` | Accent colour used for text. |
| `--color-accent-soft` | Translucent accent background. |
| `--color-accent-border` | Translucent accent border. |
| `--color-accent-ink` | Text drawn on top of the accent. |

The theme aliases are the names used by the components:

```css
:root,
[data-theme="brand"] {
  --accent: var(--color-accent);
  --accent-strong: var(--color-accent-strong);
  --accent-text: var(--color-accent-text);
  --accent-soft: var(--color-accent-soft);
  --accent-border: var(--color-accent-border);
  --accent-ink: var(--color-accent-ink);
}
```

`brand` is the default because `:root` also receives the aliases. Setting
`data-theme="brand"` is therefore optional, not required.

### Status colours

| Token | Role |
| --- | --- |
| `--color-danger` | Base danger colour. |
| `--color-danger-strong` | Filled danger button. |
| `--color-danger-hover` | Danger hover. |
| `--color-danger-text` | Danger text on a dark surface. |
| `--color-danger-soft` | Translucent danger background. |
| `--color-success` | Base success colour. |
| `--color-success-text` | Success text. |
| `--color-success-soft` | Translucent success background. |
| `--color-warning` | Base warning colour. |
| `--color-warning-text` | Warning text. |
| `--color-warning-soft` | Translucent warning background. |
| `--color-info` | Info colour; aliases the accent. |
| `--color-info-text` | Info text; aliases the accent text. |
| `--color-info-soft` | Info background; aliases the accent soft colour. |

### Typography tokens

| Token | Value |
| --- | --- |
| `--font-display` | `"Space Grotesk", "Inter", system-ui, sans-serif` |
| `--font-body` | `"Inter", system-ui, -apple-system, "Segoe UI", sans-serif` |
| `--font-mono` | `"JetBrains Mono", "SFMono-Regular", consolas, monospace` |

The type scale starts at `--text-2xs` (`0.6875rem`) and ends at `--text-5xl`
(a fluid `clamp()` between `2.6rem` and `4.25rem`). The intermediate steps are
`--text-xs`, `--text-sm`, `--text-base`, `--text-md`, `--text-lg`, `--text-xl`,
`--text-2xl`, `--text-3xl` and `--text-4xl`.

Line-height tokens: `--leading-tight` (`1.05`), `--leading-snug` (`1.25`),
`--leading-normal` (`1.65`) and `--leading-relaxed` (`1.78`).

### Spacing, layout, radii and layers

The spacing scale is a strict 4px/8px rhythm:
`--space-0`, `--space-0-5`, `--space-1`, `--space-1-5`, `--space-2`,
`--space-3`, `--space-4`, `--space-5`, `--space-6`, `--space-7`,
`--space-8`, `--space-10`, `--space-12`, `--space-16`, `--space-20`.

| Token | Value | Notes |
| --- | --- | --- |
| `--container` | `75rem` | Default container width. |
| `--container-wide` | `85rem` | Available, but no class uses it yet. |
| `--container-narrow` | `45rem` | Reading width. |
| `--gutter` | `clamp(1rem, 4vw, 2.5rem)` | Fluid side spacing. |
| `--header-height` | `4.5rem` | Sticky header height. |

Radii: `--radius-xs` (`2px`), `--radius-sm` (`4px`), `--radius-md` (`6px`),
`--radius-lg` (`10px`), `--radius-xl` (`14px`), `--radius-pill` (`999px`).

Shadows: `--shadow-sm`, `--shadow-md`, `--shadow-lg` and `--shadow-glow` are
available for new components. The shared components use borders more than
shadows.

Layers: `--z-header` (`100`) is the only z-index token. Keep new layers close to
the existing scale instead of inventing values such as `9999`.

Tracking: `--tracking-wide` (`0.1em`), `--tracking-wider` (`0.18em`) and
`--tracking-widest` (`0.24em`).

## Base element styles

`styles/styles.css` styles elements directly instead of resetting everything:

- `body` sets the page background, the two decorative radial gradients, the
  body font, the base size and the normal line-height.
- `h1`–`h6` use `--font-display`, weight `600`, tight leading and slightly
  negative tracking. Their sizes step down from `--text-5xl` to `--text-base`.
- `p` uses `--leading-normal`.
- `strong`, `b`, `small`, `em`, `i`, `blockquote`, `cite`, `code`, `kbd`,
  `samp`, `pre`, `mark`, `a`, `ul`, `ol`, `table`, `hr`, `::selection` and
  `:focus-visible` have small, targeted rules.
- Inline `code` uses a bordered chip; `pre code` removes the chip because the
  block already provides the frame.
- Focus rings use `:focus-visible`, so mouse clicks do not show the ring.

The base layer is deliberately small. It does not apply a universal margin
reset, a global `box-sizing: border-box` or a form-control reset. Components
bring their own spacing and borders; new interactive elements should use `.btn`
or an explicit component style.

## Global utilities from `styles/styles.css`

| Class | What it does |
| --- | --- |
| `.visually-hidden` | Hides text visually but keeps it available to screen readers. |
| `.text-sm` | Uses the small text size (`--text-sm`). |
| `.text-muted` | Uses the secondary text colour (`--color-text-muted`). |

## Layout classes from `styles/shared.css`

| Class | What it does |
| --- | --- |
| `.container` | Centres content and caps its width with `--container` and a fluid gutter. |
| `.container--narrow` | Replaces `--container` with `--container-narrow` for long reading. |
| `.section` | Adds fluid vertical space around a section with `clamp()`. |
| `.section--tight` | Reduces section spacing. |
| `.section--flush-top` | Removes top section padding. |
| `.section__header` | Groups an eyebrow, title and lead; caps the header at `62ch`. |
| `.section__title` | Uses the large `--text-4xl` section heading. |
| `.grid` | Creates a CSS Grid with the standard gap. |
| `.grid--3` | Auto-fitting grid: `repeat(auto-fit, minmax(min(100%, 17rem), 1fr))`. It is not a hard-coded three-column grid. |
| `.grid--sidebar` | One column below `900px`; sidebar plus content from `900px` up. The sidebar is between `14rem` and `18rem`. |
| `.stack` | Vertical flex column with a gap; the gap can be overridden with `--stack-gap`. |
| `.stack--sm` | Smaller vertical gap (`--space-1-5`). |
| `.stack--lg` | Larger vertical gap (`--space-5`). |
| `.cluster` | Wrapping horizontal row for buttons, labels and metadata. |
| `.surface` | Bordered, rounded panel used by cards, sidebars, callouts and article bodies. |
| `.eyebrow` | Small mono, uppercase section label. It has no decorative dot. |
| `.lead` | Larger introductory paragraph, capped at `65ch`. |

The layout breakpoints are:

- `900px` for `.grid--sidebar`.
- `800px` and `1100px` for `.site-footer__main`.

## Buttons

| Class | What it does |
| --- | --- |
| `.btn` | Base style for links or buttons that look like buttons. |
| `.btn--primary` | Main filled action using the current accent. |
| `.btn--secondary` | Secondary outlined action. |
| `.btn--ghost` | Quiet action with no border or background. |
| `.btn--danger` | Filled destructive action. |
| `.btn--danger-outline` | Outlined destructive action. |
| `.btn--delete` | Destructive action with a soft background, intended for the delete icon. |
| `.btn--link` | Text-style action with no button padding or border. |
| `.btn--sm` | Smaller button size. |
| `.btn--lg` | Larger button size. |
| `.btn--icon` | Square icon-only button. Combine with `.btn--sm` for a smaller square. |

The button variants expose `--btn-bg-hover`, `--btn-fg-hover` and
`--btn-border-hover` values. To add hover feedback, add a `.btn:hover` rule that
uses those properties. Disabled buttons should also be styled explicitly when a
page needs them.

## Badges, tags and status

| Class | What it does |
| --- | --- |
| `.badge` | Base pill label. |
| `.badge--accent` | Accent-coloured badge. |
| `.badge--outline` | Transparent badge with a strong border. |
| `.badge--solid` | Filled accent badge with maximum contrast. |
| `.tag-list` | Resets a list and lets tags wrap. |
| `.tag` | Base topic tag, lighter than a badge. |
| `.tag--accent` | Accent-coloured tag. |
| `.status` | Compact uppercase state label. |
| `.status--success` | Positive or completed state. |
| `.status--warning` | State that needs attention. |
| `.status--danger` | Serious or failed state. |
| `.status--info` | Informational state based on the accent. |

Use the accent, outline or solid badge variants. Use `.status--*` when the
colour carries a state.

## Navigation and breadcrumbs

| Class | What it does |
| --- | --- |
| `.site-header` | Sticky header with a translucent background and bottom border. |
| `.site-nav__inner` | Lays out the brand, links and optional actions in one row. |
| `.brand` | Styles the project identity link. |
| `.brand__mark` | Optional square monogram. |
| `.brand__copy` | Wrapper for the project name. It inherits from `.brand`; the footer adds a specific rule for it. |
| `.brand__sub` | Small uppercase subtitle. |
| `.site-nav__links` | Removes list styling and pushes the links to the right. |
| `.site-nav__link` | Styles one desktop navigation link. |
| `.site-nav__actions` | Holds optional header actions. |
| `.nav-toggle` | Summary-style control reserved for a future mobile drawer. It is not used by the current pages. |
| `.nav-toggle__bars` | Groups the three menu bars inside `.nav-toggle`. |
| `.breadcrumbs` | Inline breadcrumb list with CSS-generated `/` separators. |
| `.breadcrumbs a` | Dimmed breadcrumb links. |
| `.breadcrumbs [aria-current="page"]` | Brightens the current breadcrumb. |

Use `aria-current="page"` to mark the current page. The navigation has no
secondary sticky bar and no mobile drawer.

## Statistics and metrics

| Class | What it does |
| --- | --- |
| `.stat-grid` | Auto-fitting grid of statistics with shared hairline borders. |
| `.stat` | One statistic cell. |
| `.stat__value` | Large statistic value. |
| `.stat__label` | Small uppercase statistic label. |
| `.metric` | Standalone compact metric with its own border. |
| `.metric__value` | Very large accent value. |
| `.metric__label` | Small uppercase metric label. |

## Cards and article content

| Class | What it does |
| --- | --- |
| `.card` | Base card: vertical flex column with hidden overflow and rounded corners. |
| `.card__body` | Main card content area; fills the remaining height. |
| `.card__title` | Card heading. |
| `.card__text` | Muted card description. |
| `.card__media` | 16:9 media area with a gradient background. |
| `.topic-card` | Large clickable module card, with an accent top border. |
| `.topic-card__index` | Module number and metadata line. |
| `.topic-card__title` | Topic heading. |
| `.topic-card__text` | Topic description. |
| `.topic-card__cta` | Call-to-action text pinned to the bottom of the card. |
| `.unit-card` | Compact lesson card. |
| `.unit-card__meta` | Unit number and duration row. |
| `.unit-card__title` | Unit heading. |
| `.unit-card__text` | Unit description. |
| `.unit-card__footer` | Unit footer with a tag and an action. |
| `.article-card__tag` | Label positioned in the top-left of a card media area. |
| `.article-card__read` | Small mono reading link. |

`.article-card` is a semantic wrapper used with `.card`, for example
`class="card article-card"`. It does not have its own rule; only its child
classes are styled.

For a metadata row in a card, use `.cluster` or a `.text-sm.text-muted`
paragraph inside `.card__body`.

`data-index` is optional metadata and is not used by the CSS. The visible module
number comes from the text inside `.topic-card__index`.

## Tables, timeline and callouts

| Class | What it does |
| --- | --- |
| `.table-wrap` | Adds a scrollable, bordered frame around a table. |
| `.data-table` | Styles a data table with a caption, header row and row dividers. |
| `.timeline` | Creates the vertical line and list layout. |
| `.timeline__item` | One event, with a dot drawn by CSS. |
| `.timeline__time` | Event time or date. |
| `.timeline__title` | Event heading. |
| `.timeline__text` | Event description. |
| `.callout` | Info callout with a coloured left edge. |
| `.callout__title` | Callout heading. |
| `.callout p` | Smaller muted body copy inside a callout. |
| `.callout--success` | Success variation. |
| `.callout--warning` | Warning variation. |
| `.callout--danger` | Danger variation. |

`.data-table` has `min-width: 40rem`, so narrow windows scroll the table inside
`.table-wrap` instead of crushing the columns.

## Footer and small pieces

| Class | What it does |
| --- | --- |
| `.site-footer` | Deeper footer background with a top border. |
| `.site-footer__main` | Footer grid: one column, then two at `800px`, three at `1100px`. |
| `.site-footer__brand` | Footer brand and description column. |
| `.site-footer__text` | Muted footer body text. |
| `.site-footer__title` | Small uppercase footer column heading. |
| `.site-footer__list` | Footer list with no markers and a standard gap. |
| `.site-footer__list--grid` | Two-column footer link list. |
| `.site-footer__link` | Footer link style. |
| `.avatar` | Circular initials avatar. |
| `.avatar--sm` | Smaller avatar. |
| `.empty-state` | Dashed placeholder for an area with no content. |
| `.empty-state__icon` | Circular icon inside an empty state. |

## Component-gallery helpers

These classes are defined in the `<style>` block at the top of
`components.html`, not in `shared.css`. Do not copy them into a real page unless
you also copy that style block.

| Class | What it does |
| --- | --- |
| `.component` | Outer preview box. |
| `.component__preview` | Inner preview area with a soft radial accent. |
| `.component-index` | Horizontal index of component sections. |
| `.component-list` | Stacked preview-first layout. |
| `.component-list__name` | Caption below an example. |
| `.component-list__demo` | Full-width rendered example area. |
| `.site-header--preview` | Keeps a demo header in the normal page flow. |
| `.swatch-grid` | Grid of colour samples. |
| `.swatch` | One colour sample. |
| `.swatch__color` | Coloured block; the colour comes from an inline `--swatch`. |
| `.swatch__meta` | Name and value below a sample. |
| `.swatch__name` | Human-readable colour name. |
| `.swatch__value` | Token name and hex value. |
| `.demo-row` | Horizontal example layout. |
