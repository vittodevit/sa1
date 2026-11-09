# Simple project guide

This guide explains how to use the project without assuming that you already know HTML or CSS.
The project is static: it uses no JavaScript, framework, or build system.
It targets desktop screens; mobile media queries are intentionally omitted.

## Where to start

1. Open `components.html` in the browser. It contains examples of the components.
2. Open `article.html` to see a complete page using the same styles.
3. When you need a new page, copy the structure from `article.html`.
4. Change the text and links, but keep the existing CSS class names.

## Main files

```text
components.html    Examples of buttons, cards, tables, navbar, and footer;
                   also holds the gallery preview styles in a <style> block
article.html       Complete example article
styles/styles.css  Colours, fonts, and general rules
styles/shared.css  Layout and reusable components
docs/              Explanations for working on the project
```

## Loading the CSS

Put these two links inside `<head>`. Keep this order:

```html
<link rel="stylesheet" href="styles/styles.css">
<link rel="stylesheet" href="styles/shared.css">
```

`styles.css` comes first because it contains the colours and base rules.
`shared.css` uses them to build cards, buttons, grids, the navbar, and the footer.
`components.html` adds a local `<style>` block for the preview layout used only
by the component gallery.

## Minimum page structure

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Page title</title>
  <link rel="stylesheet" href="styles/styles.css">
  <link rel="stylesheet" href="styles/shared.css">
</head>
<body>
  <header class="site-header">
    <!-- copy the navbar from components.html -->
  </header>

  <main>
    <section class="section">
      <div class="container">
        <h1>Page title</h1>
        <p>Short introduction.</p>
      </div>
    </section>
  </main>

  <!-- copy the footer from components.html -->
</body>
</html>
```

## How to edit without breaking the style

- Change the text inside the tags, not the class names.
- Use `<section class="section">` for a new section.
- Use `<div class="container">` to keep content at the correct width.
- Use `grid--3` for a three-column layout.
- Copy an existing card example from `components.html`.
- Use `<a>` for navigation and `<button>` for an action.
- Open the page in the browser often while you work.

Read `01-css.md` for the CSS basics, `02-components.md` for copy-and-paste HTML,
and `03-notes.md` for accessibility and the final checklist.
