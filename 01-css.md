# 01 — CSS guide and complete class reference

This file explains the CSS files and documents every reusable class in them.
The project targets desktop screens: mobile media queries are intentionally
omitted, so the layout is designed to be used on a computer.

The HTML files use two stylesheets:

- `styles/styles.css` contains variables, the reset, typography, and small utilities.
- `styles/shared.css` contains layout and visual components.

`components.html` also has a small `<style>` block for the gallery previews.
Those preview classes are local to that page and are not loaded by the other
pages.

Always load them in this order:

```html
<link rel="stylesheet" href="styles/styles.css">
<link rel="stylesheet" href="styles/shared.css">
```

## How to read a class name

The project uses a simple naming pattern:

- `.card` is the main block.
- `.card__title` is a part inside that block.
- `.btn--primary` is a variation of that block.

Classes can be combined. For example, `class="grid grid--3"` means “use the
basic grid and choose the three-column version”.

## Colours and variables

Use variables instead of adding new colour values:

```css
.my-panel {
  background: var(--color-surface);
  color: var(--color-text);
  border: 1px solid var(--color-border);
  padding: var(--space-3);
}
```

Important variables include `--color-bg`, `--color-bg-deep`,
`--color-surface`, `--color-surface-2`, `--color-surface-3`,
`--color-text`, `--color-text-muted`, `--color-text-dim`,
`--color-border`, `--color-border-strong`, `--accent`, `--accent-text`,
`--accent-soft`, `--accent-border`, `--space-1` through `--space-20`,
`--container`, `--container-wide`, `--container-narrow`, and
`--header-height`.

The available themes are `data-theme="brand"`, `data-theme="threats"`,
`data-theme="privacy"`, and `data-theme="security"`. They change the accent
colour while keeping the blue surfaces consistent.

## Global utilities from `styles.css`

| Class | What it does |
| --- | --- |
| `.visually-hidden` | Hides text visually but keeps it available to screen readers. |
| `.text-sm` | Uses small text. |
| `.text-muted` | Uses the secondary text colour. |

## Layout classes from `shared.css`

| Class | What it does |
| --- | --- |
| `.container` | Centers content and limits its width. |
| `.container--narrow` | Uses the narrower reading width. |
| `.section` | Adds normal vertical space around a section. |
| `.section--tight` | Reduces section spacing. |
| `.section--flush-top` | Removes top section padding. |
| `.section__header` | Groups a section label and title. |
| `.section__title` | Styles a large section heading. |
| `.grid` | Creates a CSS Grid with the standard gap. |
| `.grid--3` | Creates a three-column auto-fit grid. |
| `.grid--sidebar` | Creates a sidebar and main-content layout. |
| `.stack` | Places children in a vertical flex column. |
| `.stack--sm` | Uses a smaller vertical gap. |
| `.stack--lg` | Uses a larger vertical gap. |
| `.cluster` | Places items in a wrapping horizontal row. |
| `.surface` | Creates a bordered content panel. |
| `.eyebrow` | Styles a small uppercase section label. |
| `.eyebrow--plain` | Removes the decorative dot from an eyebrow. |
| `.lead` | Styles a larger introductory paragraph. |

## Buttons, badges, tags, and status

| Class | What it does |
| --- | --- |
| `.btn` | Base style for links or buttons that look like buttons. |
| `.btn--primary` | Main filled action. |
| `.btn--secondary` | Secondary outlined action. |
| `.btn--ghost` | Quiet action with little visual weight. |
| `.btn--danger` | Red destructive action. |
| `.btn--danger-outline` | Outlined destructive action. |
| `.btn--delete` | Delete action with an icon. |
| `.btn--link` | Button that looks like a text link. |
| `.btn--sm` | Smaller button size. |
| `.btn--lg` | Larger button size. |
| `.btn--icon` | Makes a square icon-only button. |
| `.badge` | Base style for a short label. |
| `.badge--accent` | Uses the general accent colour. |
| `.badge--threats` | Uses the threats colour. |
| `.badge--privacy` | Uses the privacy colour. |
| `.badge--security` | Uses the security colour. |
| `.badge--outline` | Uses an outlined badge style. |
| `.badge--solid` | Uses a stronger filled badge style. |
| `.badge--dot` | Adds a small status dot. |
| `.tag-list` | Arranges several tags in a row. |
| `.tag` | Base style for a topic tag. |
| `.tag--accent` | Accent-coloured tag. |
| `.tag--threats` | Threats-coloured tag. |
| `.tag--privacy` | Privacy-coloured tag. |
| `.tag--security` | Security-coloured tag. |
| `.status` | Base style for a state label. |
| `.status--success` | Positive or completed state. |
| `.status--warning` | State that needs attention. |
| `.status--danger` | Serious or failed state. |
| `.status--info` | Informational state. |

## Navigation classes

| Class | What it does |
| --- | --- |
| `.site-header` | Main sticky header background and border. |
| `.site-nav__inner` | Lays out the brand and navigation links. |
| `.brand` | Styles the project identity link. |
| `.brand__mark` | Styles the small logo mark. |
| `.brand__copy` | Holds the project name. |
| `.brand__sub` | Holds the smaller project subtitle. |
| `.site-nav__links` | Removes list styling and lays out navigation links. |
| `.site-nav__link` | Styles one navigation link. |
| `.site-nav__actions` | Holds optional header actions. |
| `.nav-drawer` | Legacy small-screen navigation; hidden in the desktop-only layout. |
| `.nav-toggle` | Button-like summary for the legacy drawer. |
| `.nav-toggle__bars` | Groups the three menu bars. |
| `.nav-drawer__panel` | Opened panel of the legacy drawer. |
| `.nav-drawer__list` | List inside the legacy drawer. |
| `.nav-drawer__link` | Link inside the legacy drawer. |
| `.subnav` | Sticky secondary navigation row. |
| `.subnav__list` | List used by the secondary navigation. |
| `.subnav__link` | Link in the secondary navigation. |
| `.breadcrumbs` | Styles a breadcrumb list. |
| `.is-active` | Marks the current navigation item. |

## Statistics and metrics

| Class | What it does |
| --- | --- |
| `.stat-grid` | Grid for several statistics. |
| `.stat` | One statistic block. |
| `.stat__value` | Large statistic number. |
| `.stat__label` | Statistic description. |
| `.metric` | Compact metric component. |
| `.metric__value` | Large metric value. |
| `.metric__label` | Metric description. |

## Cards and article content

| Class | What it does |
| --- | --- |
| `.card` | Base card. |
| `.card__body` | Main card content area. |
| `.card__meta` | Small information row in a card. |
| `.card__title` | Card heading. |
| `.card__text` | Card description. |
| `.card__media` | Top media or visual area. |
| `.topic-card` | Card for a main project topic. |
| `.topic-card__index` | Topic number and small metadata. |
| `.topic-card__title` | Topic heading. |
| `.topic-card__text` | Topic description. |
| `.topic-card__cta` | Topic action text. |
| `.unit-card` | Card for a smaller learning unit. |
| `.unit-card__meta` | Unit number and reading time. |
| `.unit-card__title` | Unit heading. |
| `.unit-card__text` | Unit description. |
| `.unit-card__footer` | Unit actions and tags. |
| `.article-card` | Wrapper class for an article card (use it with `.card`). |
| `.article-card__tag` | Article label inside the media area. |
| `.article-card__read` | Article reading link. |

## Tables, timelines, and messages

| Class | What it does |
| --- | --- |
| `.table-wrap` | Adds safe horizontal overflow around a table. |
| `.data-table` | Styles a project data table. |
| `.timeline` | Creates the timeline layout and line. |
| `.timeline__item` | One timeline event. |
| `.timeline__time` | Event time or date. |
| `.timeline__title` | Event heading. |
| `.timeline__text` | Event description. |
| `.callout` | Highlighted information box. |
| `.callout__title` | Callout heading. |
| `.callout--success` | Positive callout variation. |
| `.callout--warning` | Warning callout variation. |
| `.callout--danger` | Critical callout variation. |

## Footer and small pieces

| Class | What it does |
| --- | --- |
| `.site-footer` | Footer background and top border. |
| `.site-footer__main` | Main footer grid. |
| `.site-footer__brand` | Footer project identity area. |
| `.site-footer__text` | Footer description or plain text. |
| `.site-footer__title` | Footer column heading. |
| `.site-footer__list` | Footer link list. |
| `.site-footer__list--grid` | Two-column footer link list. |
| `.site-footer__link` | Footer link style. |
| `.avatar` | Circular initials avatar. |
| `.avatar--sm` | Smaller avatar. |
| `.empty-state` | Placeholder when there is no content. |
| `.empty-state__icon` | Icon area inside an empty state. |

## Component-gallery helper classes

These classes are mainly used by `components.html` to present examples. The
preview classes (`.component`, `.component__preview`, `.component-list`,
`.component-list__name`, `.component-list__demo`, and
`.site-header--preview`) are defined in the `<style>` block inside
`components.html`. The remaining helpers below are defined in
`styles/shared.css`.

| Class | What it does |
| --- | --- |
| `.component` | Outer preview box. |
| `.component__preview` | Inner preview area. |
| `.component-index` | Links to component sections. |
| `.component-list` | Stacked preview-first layout with a full-width example. |
| `.component-list__name` | Name/caption below the example. |
| `.component-list__demo` | Full-width rendered example area. |
| `.site-header--preview` | Keeps a demo header inside the page flow. |
| `.swatch-grid` | Grid of colour samples. |
| `.swatch` | One colour sample. |
| `.swatch__color` | Coloured part of a sample. |
| `.swatch__meta` | Name and value below a sample. |
| `.swatch__name` | Human-readable colour name. |
| `.swatch__value` | Hex value and variable name. |
| `.demo-row` | Horizontal example layout. |
