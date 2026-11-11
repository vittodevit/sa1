# 03 — Simple rules for working well

## Readable HTML

- Use one `<main>` per page.
- Use `header`, `nav`, `main`, `section`, `article` and `footer` in the right
  place.
- Use one `<h1>` for the page, then `<h2>` and `<h3>` for sections.
- Add `aria-label` to navigation when it helps explain its purpose.
- Use `<a>` for links and `<button>` for actions.
- Use `aria-current="page"` on the link or breadcrumb item for the current page.

## Working with the CSS

- Load `css/styles.css` first, then `css/shared.css`.
- The `brand` palette is the default. The `data-theme="brand"` attribute is
  optional because `:root` already provides the accent aliases.
- The build is desktop-first. The layout adapts at `900px` for the article
  sidebar and at `800px` / `1100px` for the footer. There is no mobile drawer.
- Use the tokens from `css/styles.css` instead of raw colours, spacing values and
  font sizes.

## Links

A link to an id must use the same name:

```html
<a href="#privacy">Go to privacy</a>
<section id="privacy">
  <h2>Privacy</h2>
</section>
```

If the id does not exist, the link will not go anywhere. When copying a card or
a navbar, always check its `href` values.

## Class names

This project uses understandable names:

- `.card` is the main block;
- `.card__title` is the title inside the card;
- `.btn--primary` is a different button version.

The pattern is `block__part` for an internal part and `block--variant` for a
different version. Layout helpers and utilities are outside BEM:
`.container`, `.grid`, `.stack`, `.cluster`, `.surface`, `.visually-hidden`,
`.text-sm` and `.text-muted`.

## Before submitting

1. Open every page in the browser.
2. Check that the navbar and footer are present.
3. Test the main links and confirm that they go to the right place.
4. Check that text does not overflow its cards or table cells.
5. Check the page at desktop widths and around the layout breakpoints
   (`800px`, `900px`, `1100px`).
6. Check that the page still looks correct without a network connection; the
   Google Fonts import falls back to the system font stacks.
7. Do not add duplicate CSS: search for an existing class first.
8. Do not copy the gallery-only classes from `components.html` into a real page
   unless you also copy its local `<style>` block.

## Adding a component

First copy a similar component from `components.html`. If it is not enough:

1. Choose a simple BEM name.
2. Add the rule to `css/shared.css`.
3. Use the existing colour, spacing, radius and typography variables.
4. Add an example to `components.html`.
5. Test the result at the normal desktop widths and at the layout breakpoints.

```css
.note {
  padding: var(--space-3);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-md);
  background: var(--color-surface);
  color: var(--color-text-muted);
}
```

`components.html` should remain the main reference. A colleague should be able
to copy a component from it without having to guess how it works.

The base layer is deliberately small: it does not apply a universal margin
reset, a global `box-sizing: border-box` or a form-control reset. New
interactive elements should use `.btn` or an explicit component rule.
