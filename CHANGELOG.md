# Changelog

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
