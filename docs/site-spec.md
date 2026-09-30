# factory.brooswit.nexus and blog.brooswit.nexus: spec

Written at handover (2026-09-29). Everything below is already live (website v0.1.10, blog v0.1.2); keep it true and use it as the acceptance list for future changes. Brooswit reviews wording and visuals.

## factory.brooswit.nexus (repo `website`)

Top to bottom, all full viewport width, no gaps or side margins:

1. Factory logo (`assets/factory-logo.png`, 1600px wide), full width, at the very top.
2. Header banner (`assets/factoryheader.jpg`, 1600px), full width.
   No visible text under it: the `h1` "Brooswit Factory" is kept inside `#top` as a screen-reader-only element (1px, clipped, not `display:none`), so it hides with the header when a product is selected and leaves no gap or band under the banner.
3. Product row (directly after the banner, 0px gap): drovr, butchr, cleavr in three equal columns (`assets/*-logo.png`, 640px, square). Three equal columns in one row at ALL widths, including 390px phones (no stacking).
4. Info area below the row, only when a product is selected. Nothing else below.

Product logos (buttons, `aria-expanded`, keyboard operable):

- Dim at first (`filter: brightness(.45)`); full brightness on hover (only where `(hover:hover)`) and on keyboard focus. On touch, the selected logo is the only bright one.
- Click selects: `assets/selected.png` overlays that logo (`::after`, pointer-events off, same box as the logo: `position:absolute; inset:0; width:100%; height:100%`, image stretched with `background-size:100% 100%`), the logo stays bright, and its info section shows below. One selected at a time; selecting another moves the overlay and dims the first.
- Clicking the selected logo again does nothing: selection changes only when a different product is clicked, and nothing is ever unselected by a click (a page reload returns to the start state). `aria-expanded` stays correct.
- While any product is selected, the factory logo and header banner are hidden (`body.has-selection #top {display:none}`) so the product row is at the top; the page scrolls to the top on every change of selection (not on a repeat click) so the layout does not jump. They stay hidden until the page is reloaded.
- Start with nothing selected.

Info area:

- Full viewport width, dark panel, with a decorative stone-texture border down the left and right edges: `assets/border.png` (53px wide, PNG8 with alpha, ~11 KB) tiled `repeat-y` in `#info::before` (left, as is) and `#info::after` (right, mirrored with `transform:scaleX(-1)` because the image is not left-right symmetric). Edge width `clamp(24px,6vw,53px)` (`--edge`), scaled proportionally on phones; `#info` has matching side padding so text never sits on the border.
- Text column max 64rem, centered, padded inside; body 1.25 to 1.6rem, headings up to 3.4rem, line height 1.65.
- Content per product (Brooswit reviews the wording; keep it 2 to 4 lines). Each section has `aria-label="<product>"` and its `h2` is the tagline, exactly: drovr "Ever onward...", butchr "It's a messy job, but someone's gotta do it...", cleavr "Now you're the butcher..." (three dots, straight apostrophes; wraps balanced, no overflow at 390px).
  - drovr (Brooswit's exact wording): lead line "A harness that wraps Herdr" ("Herdr" links to https://herdr.dev), then a real `ul` of three `li`: "Automatically handles dialogs so your agents are never blocked." / "Automatically handles development/experimental options to unlock all capabilities" (no trailing period, on purpose) / "Monitors for scenarios where agents get blocked, but Herdr doesn't catch it." / "Provides more nuanced state management" / "Lizard mode 🦎" (U+1F98E, no trailing periods on the last two). Link: https://github.com/brooswit-factory/drovr
  - butchr: the software factory daemon; watches Jira, runs one AI agent per matching ticket, pushes ticket changes to agents, live view with a terminal per agent. Link: https://github.com/brooswit-factory/butchr
  - The drovr and butchr "<product> on GitHub" links (`a.repo`) carry the product icon (`assets/drovr-icon.png`, `assets/butchr-icon.png`, 96px PNG8 shown at 48x48, `alt=""` because the link text names the product) inside the same `<a>`, vertically centered with the text.
  - cleavr: Chrome extension that slides a butchr agent panel in from the side of the page with a live terminal. PRIVATE repo: no links; the text says "Not publicly available yet." No link or icon yet (Brooswit publishes it later; the manager says when to add the link, icon and release download).
- Without JS: a `<noscript>` line links the drovr and butchr repos.

Type and palette: Cinzel Decorative 700 (headings: every `h2`) and IM Fell English 400 (body), used on all visible text. The body stack ends with an emoji fallback (`"Apple Color Emoji","Segoe UI Emoji","Noto Color Emoji"`, then Georgia, serif) so emoji render without changing the body face, SIL OFL, self-hosted latin woff2 in `fonts/` with `OFL-*.txt` licenses; dark palette (`--bg:#0d0b09`, panel `#16110d`, text `#eadfc4`, gold `#d9a441`, `#7a5a1e`, links `#f0c56a`). Must work at 390px width with no horizontal scroll.

Files: `CNAME` (factory.brooswit.nexus), `.nojekyll`, `index.html`, `assets/`, `fonts/`, `CHANGELOG.md`, `package.json`, `.github/workflows/ci.yml` (semver/changelog gate).

## blog.brooswit.nexus (repo `blog`)

One static `index.html`: full-width blog image (`assets/blog.jpg`, from `~/Downloads/blog.png`, 1600px JPEG under 500 KB), then an `h1` "Under construction" and an `h2` "Pardon our mess." (Cinzel Decorative, gold) and one body line (IM Fell English) linking the factory homepage, same fonts and palette as the website. Nothing else until Brooswit asks.

## Verify after every deploy

`curl -sI` both sites (200), fetch the page and check the changed markup is served, screenshot at 1400px and 390px, and for overlay/layout changes measure the boxes (overlay vs logo) with Puppeteer and run a positive control (a deliberately broken copy must report a mismatch).

## Open (not for the agent to decide)

- Cleavr distribution: Brooswit decided GitHub Releases, but the repo is private. Options: make the repo public; a public releases-only repo; leave private for now. Until decided, keep Cleavr unlinked.
