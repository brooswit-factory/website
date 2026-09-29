# Changelog

## 0.1.5

### Fixed

- FACTORY-539: the selected overlay always covers exactly its logo. The logo buttons are now explicitly full width of their grid cell (not content-sized, which some browsers do for buttons), and the overlay is pinned to 100% width and height of the button with the image stretched to fit.

## 0.1.4

### Changed

- FACTORY-539: dark-fantasy type and palette. Cinzel (headings) and EB Garamond (body), both SIL OFL, self-hosted as latin woff2 in `fonts/` with their licenses (no third-party font requests). The info sections are full width with much larger text and a gold double border down the left and right edges; the page background is dark to match. Works at phone widths.

## 0.1.3

### Changed

- FACTORY-539: product logos start dimmed and brighten on hover or keyboard focus. Clicking one overlays `assets/selected.png` on it (pointer events off) and keeps it bright until another is selected; the overlay and brightness move with the selection. On touch devices there is no hover, so the selected logo is the only bright one. The factory logo and header are unchanged. `aria-expanded` is kept on the buttons.

## 0.1.2

### Changed

- FACTORY-539: homepage order. The factory logo moves to the very top (full width), then the header banner (full width), then the drovr, butchr and cleavr logos in three equal columns. The tagline and the Cleavr releases link below the logos are removed; the logos no longer link to the repos directly.
- FACTORY-539: clicking a product logo reveals an info section below the logos (one at a time; click again to collapse). Plain HTML/CSS/JS, logos are buttons with `aria-expanded`. Blurbs plus links to the drovr and butchr repos; cleavr is private, so it has a blurb and no links. Without JS, a fallback links the drovr and butchr repos.

## 0.1.1

### Changed

- FACTORY-539: homepage layout. The header stays full width; the drovr, butchr and cleavr logos sit in a row of three equal columns filling the viewport (stacked on phones); the factory logo is full width below them. Logo assets re-exported at 640px and the factory logo at 1600px.

## 0.1.0

### Added

- FACTORY-537: static homepage for factory.brooswit.nexus: banner, factory logo, butchr/cleavr/drovr logos linking to their repos, and a link to the Cleavr releases. Served by GitHub Pages from `main`; the `CNAME` file sets the custom domain.
