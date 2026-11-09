# 03 — Simple rules for working well

## Readable HTML

- Use one `<main>` per page.
- Use `header`, `nav`, `main`, `section`, `article`, and `footer` in the right place.
- Use one `<h1>` for the page, then `<h2>` and `<h3>` for sections.
- Add `aria-label` to navigation when it helps explain its purpose.
- Use `<a>` for links and `<button>` for actions.

## Links

A link to an id must use the same name:

```html
<a href="#privacy">Go to privacy</a>
<section id="privacy">
  <h2>Privacy</h2>
</section>
```

If the id does not exist, the link will not go anywhere. When copying a card or
navbar, always check its `href` values.

## Class names

This project uses understandable names:

- `.card` is the main block;
- `.card__title` is the title inside the card;
- `.btn--primary` is a different button version.

The pattern is `block__part` for an internal part and `block--variant` for a
different version.

## Before submitting

1. Open every page in the browser.
2. Check that the navbar and footer are present.
3. Test the main links and confirm that they go to the right place.
4. Check that text does not overflow its cards.
5. Check the page at desktop widths. The site is desktop-only and does not
   include mobile media queries.
6. Do not add duplicate CSS: search for an existing class first.

## Adding a component

First copy a similar component from `components.html`. If it is not enough:

1. choose a simple name;
2. add the rule to `styles/shared.css`;
3. use the existing colour and spacing variables;
4. add an example to the components page;
5. test the result in the browser.

```css
.note {
  padding: var(--space-3);
  border: 1px solid var(--color-border);
  background: var(--color-surface);
}
```

`components.html` should remain the main reference. A colleague should be able
to copy a component from it without having to guess how it works.
