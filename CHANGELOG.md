# Changelog

All notable changes to [sciflux.tech](https://sciflux.tech) are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.1.0] - 2026-11-07

### Added
- Track each tab change as a separate GA4 `page_view`, titled `Sciflux · <tab>`.
- Footer privacy disclosure built on a native `<details>` element. It works without JavaScript and closes on outside click or <kbd>Esc</kbd>.
- Custom `404.html` matching the site's design, with `noindex` and root-relative asset paths.
- `_config.yml` excluding `CHANGELOG.md` and `README.md` from the GitHub Pages build.
- This changelog.

### Changed
- Fonts: merge Schibsted Grotesk and Atkinson Hyperlegible Next into a single Google Fonts request, and lazy-load Noto Sans JP only when Japanese is active.
- Bump the stylesheet cache-busting query to `styles.css?v=4`.

### Fixed
- GA4 no longer writes `_ga` / `_ga_*` cookies. GA4 ignores `client_storage: 'none'`, so `document.cookie` is shadowed with an in-memory jar before `gtag.js` loads.[^cookieless]
- The privacy popover no longer overflows the viewport on narrow screens (≤ 640 px).

> [!NOTE]
> **Why cookieless?** Privacy first. We want to know how many people visit and which sections they read, not who they are. Nobody enjoys cookie banners, and visitors shouldn't have to trade tracking for reading a page.
>
> Without a persistent ID, GA4 can't link visits by the same person, so each visit is anonymous and counts as a new user. That's a deliberate trade-off: returning-visitor metrics go away, while totals, page views, geography and acquisition stay intact.

> [!WARNING]
> The cookie override is a workaround, not a supported GA4 feature. If visits stop appearing in Analytics after a `gtag.js` update, check it first.

## [2.0.0] - 2026-11-06

### Added
- Five-tab site: Home, Technology, Impact, About, Investors.
- Japanese localisation (`ja`) with a header language switch.
- Hash-routed tabs implemented in CSS (`:target`, `:has()`). Navigation works with JavaScript disabled.
- `<noscript>` fallbacks: a static counter line, a `mailto:` contact link, and JS-only widgets hidden.
- Open Graph and Twitter Card metadata.
- `favicon.svg`: the "Sf" monogram cut from the wordmark.

### Changed
- Responsive header: two rows on mobile, with a horizontally scrollable tab bar.
- Technology figure: fixed canvas height and a two-column readout below 560 px.

### Removed
- The previous single-page holding site.

[^cookieless]: Approach from [Stack Overflow #71424887, answer 1](https://stackoverflow.com/questions/71424887/cookieless-google-analytics-v4-still-generates-ga-cookie).

[2.1.0]: https://github.com/sjoemetsa/sciflux/compare/v2.0.0...v2.1.0
[2.0.0]: https://github.com/sjoemetsa/sciflux/releases/tag/v2.0.0
