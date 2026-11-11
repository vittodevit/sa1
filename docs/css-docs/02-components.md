# 02 — HTML components

This file explains every component demonstrated in `components.html`. The
examples use the classes defined in `css/styles.css` and
`css/shared.css`.

The safest workflow is:

1. Find the example you need in `components.html`.
2. Copy the complete HTML block.
3. Keep the class names unchanged.
4. Change the text, numbers and links.
5. Open the page in a browser and check the result.

## Page structure

Every page should have a header, one main content area and a footer:

```html
<header class="site-header">...</header>
<main id="main">...</main>
<footer class="site-footer">...</footer>
```

The `id="main"` gives in-page links a target. Use only one `<main>` on a page.

Load the stylesheets in this order:

```html
<link rel="stylesheet" href="css/styles.css">
<link rel="stylesheet" href="css/shared.css">
```

The pages are desktop-first. The article sidebar and the footer adapt at
`900px`, `800px` and `1100px` respectively. There is no mobile navigation
drawer.

## Navbar

The navbar contains the project name and the topic links:

```html
<header class="site-header">
  <nav class="container site-nav__inner" aria-label="Main navigation">
    <a class="brand" href="...">
      <span class="brand__copy">
        CyberAware
      </span>
    </a>

    <ul class="site-nav__links">
      <li><a class="site-nav__link" href="...">Home</a></li>
      <li><a class="site-nav__link" href="...">Common Threats</a></li>
      <li><a class="site-nav__link" href="...">Malware</a></li>
      <li><a class="site-nav__link" href="...">Privacy</a></li>
      <li><a class="site-nav__link" href="...">Famous Incidents</a></li>
      <li><a class="site-nav__link" href="...">Good Security Practices</a></li>
      <li><a class="site-nav__link" href="...">Secure Communication</a></li>
      <li><a class="site-nav__link" href="...">Authentication</a></li>
    </ul>
  </nav>
</header>
```

The current page can be marked with `aria-current="page"` on its link:

```html
<a class="site-nav__link" href="article.html" aria-current="page">Article</a>
```

The attribute describes the current page for assistive technology. Add a visual
rule if the navigation needs a visible active state.

## Footer

The footer repeats the main topics:

```html
<footer class="site-footer">
  <div class="container site-footer__main">
    <div class="site-footer__brand">
      <span class="brand__copy">
        CyberAware
        <span class="brand__sub">USI · Software Atelier I</span>
      </span>
      <p class="site-footer__text">
        One click can compromise everything. Awareness can protect it all.
      </p>
    </div>

    <div>
      <h2 class="site-footer__title">Modules</h2>
      <ul class="site-footer__list site-footer__list--grid">
        <li><a class="site-footer__link" href="#cards">Common Threats</a></li>
        <li><a class="site-footer__link" href="#cards">Malware</a></li>
        <li><a class="site-footer__link" href="#cards">Privacy</a></li>
        <li><a class="site-footer__link" href="#cards">Famous Incidents</a></li>
        <li><a class="site-footer__link" href="#cards">Good Security Practices</a></li>
        <li><a class="site-footer__link" href="#cards">Secure Communication</a></li>
        <li><a class="site-footer__link" href="#cards">Authentication</a></li>
      </ul>
    </div>

    <div>
      <h2 class="site-footer__title">Project</h2>
      <ul class="site-footer__list">
        <li><span class="site-footer__text">Software Atelier I</span></li>
        <li><span class="site-footer__text">Group 3</span></li>
        <li><span class="site-footer__text">USI 2026/27</span></li>
      </ul>
    </div>
  </div>
</footer>
```

The footer is one column by default, two columns from `800px` and three columns
from `1100px`.

## Section heading and containers

```html
<section class="section">
  <div class="container">
    <div class="section__header">
      <p class="eyebrow">01 · Topic</p>
      <h2 class="section__title">Section title</h2>
      <p class="lead">A short explanation of the section.</p>
    </div>
  </div>
</section>
```

Use `.container--narrow` for long-form reading, `.section--tight` when the
section needs less space, and `.section--flush-top` to remove the top spacing.

## Buttons

Use an anchor for navigation and a button for an action:

```html
<a class="btn btn--primary" href="article.html">Read article</a>
<a class="btn btn--secondary" href="#cards">Secondary link</a>
<button class="btn btn--danger" type="button">Delete</button>
```

Add `.btn--sm`, `.btn--lg` or `.btn--icon` for size and layout variations:

```html
<a class="btn btn--primary btn--lg" href="article.html">Read the article</a>
<button class="btn btn--secondary btn--icon" type="button" aria-label="Add item">+</button>
```

Use `.btn--delete` when the button includes the delete SVG icon. The icon should
be decorative:

```html
<button class="btn btn--delete" type="button">
  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"
       aria-hidden="true" focusable="false">
    <path d="M4 7h16M9 7V5h6v2M6 7l1 13h10l1-13M10 11v6M14 11v6"/>
  </svg>
  Delete
</button>
```

## Badges, tags and status labels

Use the accent, outline and solid badges, plus the accent tag and the status
variants:

```html
<div class="cluster">
  <span class="badge badge--accent">Featured</span>
  <span class="badge badge--outline">Theory</span>
  <span class="badge badge--solid">New</span>
</div>

<ul class="tag-list">
  <li><span class="tag tag--accent">Privacy</span></li>
  <li><span class="tag">Security</span></li>
  <li><span class="tag">Encryption</span></li>
</ul>

<div class="cluster">
  <span class="status status--info">Draft</span>
  <span class="status status--success">Verified</span>
  <span class="status status--warning">Review</span>
  <span class="status status--danger">Critical</span>
</div>
```

Use `.status--*` when the colour communicates a state.

## Breadcrumbs

Breadcrumbs show where the current page is:

```html
<nav aria-label="Breadcrumb">
  <ol class="breadcrumbs">
    <li><a href="components.html">Home</a></li>
    <li><a href="components.html#cards">Modules</a></li>
    <li><span aria-current="page">Current article</span></li>
  </ol>
</nav>
```

The `/` separators are generated by CSS. The last item is brightened by the
`aria-current="page"` selector.

## Cards

### Basic card

```html
<article class="card">
  <div class="card__body">
    <p class="text-sm text-muted">Module 01 · 8 min</p>
    <h3 class="card__title">Card title</h3>
    <p class="card__text">A short description.</p>
    <a class="btn btn--link btn--sm" href="#cards">Open</a>
  </div>
</article>
```

For a metadata row, use a `.text-sm.text-muted` paragraph or a `.cluster` row
inside `.card__body`.

### Card with media

```html
<article class="card article-card">
  <div class="card__media">
    <span class="badge badge--accent article-card__tag">Special dossier</span>
  </div>
  <div class="card__body">
    <p class="text-sm text-muted">Threats · Module 01 · 12 min read</p>
    <h3 class="card__title">The Evolution of Modern Ransomware</h3>
    <p class="card__text">
      An introduction to ransomware, its effects, and the security lessons it teaches.
    </p>
    <a class="article-card__read" href="#cards">Read full dossier →</a>
  </div>
</article>
```

`.article-card` is a semantic wrapper used together with `.card`; it has no
separate CSS rule. The child classes `.article-card__tag` and
`.article-card__read` are styled.

### Topic card

Use `.topic-card` for the main modules:

```html
<a class="topic-card" href="#cards">
  <span class="topic-card__index">Module 01 · Threats</span>
  <h3 class="topic-card__title">Common Threats</h3>
  <p class="topic-card__text">Short topic description.</p>
  <span class="topic-card__cta">Explore section →</span>
</a>
```

`data-index` is optional metadata and is not used by the CSS. The visible module
number comes from the text inside `.topic-card__index`. The card uses the
`brand` accent.

### Unit card

Use `.unit-card` for a smaller lesson:

```html
<article class="unit-card">
  <div class="unit-card__meta">
    <span>Unit 01.1</span>
    <span>8 min</span>
  </div>
  <h3 class="unit-card__title">Common Cybersecurity Threats</h3>
  <p class="unit-card__text">
    Threat categories, attack surfaces, and basic risk evaluation.
  </p>
  <div class="unit-card__footer">
    <span class="badge badge--outline">Theory</span>
    <a class="btn btn--link btn--sm" href="#cards">Open unit →</a>
  </div>
</article>
```

## Data and statistics

```html
<div class="stat-grid">
  <div class="stat">
    <span class="stat__value">3</span>
    <span class="stat__label">Core modules</span>
  </div>
  <div class="stat">
    <span class="stat__value">8px</span>
    <span class="stat__label">Spacing rhythm</span>
  </div>
</div>

<div class="metric">
  <span class="metric__value">12</span>
  <span class="metric__label">Minutes</span>
</div>
```

Use `.stat-grid` for several statistics and `.metric` for one compact value.

## Tables

```html
<div class="table-wrap">
  <table class="data-table">
    <caption>Authentication factors</caption>
    <thead>
      <tr>
        <th scope="col">Factor</th>
        <th scope="col">Status</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><strong>Passkey</strong></td>
        <td><span class="status status--success">Verified</span></td>
      </tr>
    </tbody>
  </table>
</div>
```

Always include a `caption` and use `scope="col"` on column headings. The table
has a minimum width and scrolls inside `.table-wrap` when the window is narrow.

## Timeline

```html
<ol class="timeline">
  <li class="timeline__item">
    <p class="timeline__time">07:44 · First event</p>
    <h3 class="timeline__title">Event title</h3>
    <p class="timeline__text">What happened during this event.</p>
  </li>
  <li class="timeline__item">
    <p class="timeline__time">18:24 · Response</p>
    <h3 class="timeline__title">The spread is contained</h3>
    <p class="timeline__text">The response team limits the incident.</p>
  </li>
</ol>
```

The vertical line and the dots are drawn by CSS. Each event needs the four
child classes shown above.

## Callouts

```html
<div class="callout">
  <p class="callout__title">Editorial note</p>
  <p>Extra context or a short explanation.</p>
</div>

<div class="callout callout--warning">
  <p class="callout__title">Attention</p>
  <p>This message needs attention.</p>
</div>
```

Callout variations are `.callout--success`, `.callout--warning` and
`.callout--danger`. The base `.callout` is the neutral info state.

## Avatars and empty states

```html
<span class="avatar">CA</span>
<span class="avatar avatar--sm">G3</span>

<div class="empty-state">
  <span class="empty-state__icon" aria-hidden="true">∅</span>
  <h3>No results</h3>
  <p class="text-sm text-muted">There is nothing to show yet.</p>
</div>
```

Use `.avatar--sm` for a smaller avatar. Use `.empty-state` when a section has no
content yet instead of leaving a blank area.

## Colour swatches and gallery helpers

The component page uses `.swatch-grid`, `.swatch`, `.swatch__color`,
`.swatch__meta`, `.swatch__name` and `.swatch__value` to show the palette. The
actual colour comes from an inline custom property:

```html
<div class="swatch">
  <div class="swatch__color" style="--swatch: #91E5F6"></div>
  <div class="swatch__meta">
    <span class="swatch__name">Frosted Blue</span>
    <span class="swatch__value">#91E5F6 · --frosted-blue</span>
  </div>
</div>
```

The gallery wrappers are also local to `components.html`:
`.component`, `.component__preview`, `.component-index`, `.component-list`,
`.component-list__name`, `.component-list__demo`, `.site-header--preview` and
`.demo-row`.

All of these classes are defined in the `<style>` block at the top of
`components.html`, not in `shared.css`. Do not copy the preview wrappers into a
real page unless you also copy that style block.
