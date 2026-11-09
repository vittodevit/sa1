# 02 — HTML components

This file explains every component demonstrated in `components.html`.
The examples target desktop screens; mobile-only variations are not part of
this build.

The safest workflow is:

1. Find the example you need in `components.html`.
2. Copy the complete HTML block.
3. Keep the class names unchanged.
4. Change the text, numbers, and links.
5. Open the page in a browser and check the result.

## Page structure

Every page should have a header, one main content area, and a footer:

```html
<header class="site-header">...</header>
<main id="main">...</main>
<footer class="site-footer">...</footer>
```

The `id="main"` gives in-page links a target. Use only one `<main>` on a page.

## Navbar

The navbar contains the project name and the topic links.

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

Use `.is-active` only on the current page or current section. `#cards` is an
example target; replace it with a real id when you create a new section.

## Footer

The footer repeats the same topics as the navbar:

```html
<footer class="site-footer">
  <div class="container site-footer__main">
    <div class="site-footer__brand">
      <a class="brand" href="components.html">
        <span class="brand__copy">
          CyberAware
          <span class="brand__sub">USI · Software Atelier I</span>
        </span>
      </a>
      <p class="site-footer__text">One click can compromise everything. Awareness can protect it all.</p>
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
      </ul>
    </div>
  </div>
</footer>
```

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

Use `.section--tight` when the section needs less space, and
`.section--flush-top` to remove the top spacing.

## Buttons

Use an anchor for navigation and a button for an action:

```html
<a class="btn btn--primary" href="article.html">Read article</a>
<a class="btn btn--secondary" href="#cards">Secondary link</a>
<button class="btn btn--danger" type="button">Delete</button>
```

Add `.btn--sm`, `.btn--lg`, or `.btn--icon` for size and layout variations.
Use `.btn--delete` when the button includes the delete SVG icon.

## Badges, tags, and status labels

```html
<div class="demo-row">
  <span class="badge badge--accent">Featured</span>
  <span class="badge badge--threats">Threats</span>
  <span class="badge badge--outline">Theory</span>
  <span class="badge badge--accent badge--dot">Live</span>
</div>

<ul class="tag-list">
  <li><span class="tag tag--privacy">Privacy</span></li>
  <li><span class="tag tag--security">Security</span></li>
</ul>

<span class="status status--success">Verified</span>
<span class="status status--warning">Review</span>
<span class="status status--danger">Critical</span>
<span class="status status--info">Draft</span>
```

Use the `--threats`, `--privacy`, and `--security` versions to match a topic.
Use status classes for the meaning of the state, not only for decoration.

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

## Cards

### Basic card

```html
<article class="card">
  <div class="card__body">
    <div class="card__meta"><span>Module 01</span><span>8 min</span></div>
    <h3 class="card__title">Card title</h3>
    <p class="card__text">A short description.</p>
    <a class="btn btn--link btn--sm" href="#cards">Open</a>
  </div>
</article>
```

### Topic card

Use `.topic-card` for the main modules:

```html
<a class="topic-card" data-theme="threats" data-index="01" href="#cards">
  <span class="topic-card__index">Module 01</span>
  <h3 class="topic-card__title">Common Threats</h3>
  <p class="topic-card__text">Short topic description.</p>
  <span class="topic-card__cta">Explore section →</span>
</a>
```

The `data-theme` value selects the topic accent and `data-index` displays the
module number.

### Unit and article cards

Use `.unit-card` for a smaller lesson and `.article-card` for a reading item.
Their child classes are `.unit-card__meta`, `.unit-card__title`,
`.unit-card__text`, `.unit-card__footer`, `.article-card__tag`, and
`.article-card__read`.

## Data and statistics

```html
<div class="stat-grid">
  <div class="stat">
    <span class="stat__value">3</span>
    <span class="stat__label">Core modules</span>
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

Always include a `caption` and use `scope="col"` on column headings.

## Timeline

```html
<ol class="timeline">
  <li class="timeline__item">
    <p class="timeline__time">07:44 · First event</p>
    <h3 class="timeline__title">Event title</h3>
    <p class="timeline__text">What happened during this event.</p>
  </li>
</ol>
```

The list creates the vertical line automatically. Each event needs the
`timeline__item`, `timeline__time`, `timeline__title`, and `timeline__text` parts.

## Callouts

```html
<div class="callout callout--warning">
  <p class="callout__title">Attention</p>
  <p>This message needs attention.</p>
</div>
```

Callout variations are `callout--success`, `callout--warning`, and
`callout--danger`.

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

Use `.avatar--sm` for a smaller avatar. Use `.empty-state` when a section has
no content yet instead of leaving a blank area.

## Colour swatches and gallery helpers

The component page uses `.swatch-grid`, `.swatch`, `.swatch__color`,
`.swatch__meta`, `.swatch__name`, and `.swatch__value` to show the palette.
It also uses `.component`, `.component__preview`, `.component-index`,
`.component-list`, `.component-list__name`, and `.component-list__demo` to
organise each example. The previews are stacked: each example takes the full
width, with its name as a small caption below it.

The preview box and `.component-list` styles live in the `<style>` block at
the top of `components.html`; the other gallery helpers are in
`styles/shared.css`. Do not copy the preview wrappers into a real page unless
you also copy that style block.

`.site-header--preview` keeps a demo navbar in the normal page flow.
`.demo-row` creates a horizontal example layout.
