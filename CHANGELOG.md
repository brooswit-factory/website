# Changelog

## 0.1.13

### Changed

- FACTORY-547: removed the visible "Brooswit Factory" title line under the header banner. The `h1` stays inside `#top` as a screen-reader-only element (1px, clipped) so the page keeps its heading; nothing visible is left in its place and the product logos follow the banner with no gap.
- FACTORY-548: the gold double border on the left and right of the info area is replaced by a stone-texture image, `assets/border.png` (from `boarder.png`, quantized to PNG8 with alpha, 137 KB to about 11 KB), tiled down each side at up to 53px wide and scaled down on phones (`clamp(24px,6vw,53px)`). The image is not left-right symmetric, so the left edge uses it as is and the right edge is mirrored (`transform:scaleX(-1)`).
- FACTORY-550: the three product logos stay in one row of three equal columns at every width, including 390px phones (the 600px stacking rule is removed). The selected overlay still covers exactly its logo.
- FACTORY-551: two more drovr bullets, "Provides more nuanced state management" and "Lizard mode 🦎" (no trailing periods). The body font stack now ends with an emoji fallback (Apple Color Emoji, Segoe UI Emoji, Noto Color Emoji) so the emoji renders; the body face is unchanged.
- `docs/site-spec.md` updated for all four.

## 0.1.12

### Changed

- FACTORY-545: the drovr section uses Brooswit's exact wording: "A harness that wraps Herdr" (Herdr links to https://herdr.dev) followed by a bulleted list of three items. The drovr and butchr "on GitHub" links now show the product icon (48px, decorative, 96px PNG8 files of about 4 KB) next to the text. Cleavr is unchanged ("Not publicly available yet."). `docs/site-spec.md` updated.

## 0.1.11

### Fixed

- FACTORY-543: the butchr tagline now reads "It's a messy job, but someone's gotta do it..." (the copy said "message", a typo). `docs/site-spec.md` updated.

## 0.1.10

### Changed

- FACTORY-542: all headings (the title line and the three tagline headings) use Cinzel Decorative 700 instead of Uncial Antiqua, which was hard to read (`t` looked like `c`). Uncial Antiqua removed (woff2, `@font-face`, preload, licence). Body stays IM Fell English. Heading sizes reduced a little because Cinzel Decorative is wide. `docs/site-spec.md` updated.

## 0.1.9

### Changed

- FACTORY-542: unmistakably dark-fantasy type. Headings use Uncial Antiqua 400 and all body text IM Fell English 400 (SIL OFL, self-hosted latin woff2 in `fonts/` with licenses), replacing Cinzel and EB Garamond (files, `@font-face` and preloads removed). Body is slightly larger and airier (1.4rem, line-height 1.7) for the Fell face. New title line under the header banner: h1 "Brooswit Factory", large, gold, centered, inside `#top` so it hides with the header when a product is selected. The info section headings are now the taglines (drovr "Ever onward...", butchr "It's a message job, but someone's gotta do it...", cleavr "Now you're the butcher..."), with `aria-label` carrying the product name. `docs/site-spec.md` updated.

## 0.1.8

### Changed

- FACTORY-542: clicking the already-selected product logo now does nothing. The selection changes only when a different product is clicked, so once a product is selected the factory logo and header stay hidden, the overlay stays on it and its info section stays open (reload to return to the start). `aria-expanded` stays correct and the page scrolls to the top only when the selection changes. Replaces the click-again-to-deselect behaviour from 0.1.6. `docs/site-spec.md` updated.

## 0.1.7

### Added

- FACTORY-541: `docs/agent-brief.md` (role and rules for agent-webdev) and `docs/site-spec.md` (current behavior of the site and blog as the acceptance list). No site change.

## 0.1.6

### Changed

- FACTORY-539: selecting a product hides the factory logo and header banner, so the product logos sit at the top with the info section below. Clicking the selected product again deselects it: all logos dim, the header and factory logo return, the info section closes. The page scrolls to the top on either change so the layout doesn't jump.

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
