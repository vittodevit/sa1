# CSS documentation

This folder documents the project's CSS as it is. The source files are:

- `styles/styles.css` — design tokens, base element styles, typography and utilities.
- `styles/shared.css` — layout primitives and reusable components.
- `components.html` — the component catalogue.
- `article.html` — an example article page.

Files in this folder:

- `01-css.md` — CSS guide, token reference and complete class reference.
- `02-components.md` — copyable HTML examples for every component.
- `03-notes.md` — practical rules for editing and checking pages.

The pages are desktop-first. The layout adapts at `900px` for the article
sidebar and at `800px` / `1100px` for the footer. 

The `brand` palette is the default. The accent aliases are available from
`:root`, so `data-theme="brand"` is optional.
