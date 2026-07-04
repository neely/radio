# The Dial

A personal web radio player — one page, no frameworks, no build step.

Live at **[radio.benneely.com](https://radio.benneely.com)**

---

## What it is

A curated list of community, college, and independent radio stations that I actually
listen to. Stations are browsable via a rotary drum tuner; clicking a card plays the
stream directly in the browser. Nothing leaves the page.

Design constraint: only stations with a real, public, embeddable stream URL make the
main grid. Stations without one (typically those behind NPR's Brightspot CMS or similar
JS-wrapped players) appear as text links in the footer — not penalized, just a technical
reality.

## Current stations

| Station | Freq | City |
|---------|------|------|
| KZSC | 88.1 FM | Santa Cruz, CA |
| WNCW | 88.7 FM | Spindale, NC |
| The Current | 89.3 FM | Minneapolis, MN |
| WRFG | 89.3 FM | Atlanta, GA |
| KCRW | 89.9 FM | Santa Monica, CA |
| WEVL | 89.9 FM | Memphis, TN |
| Studio One | 90.1 FM | Des Moines, IA |
| KEXP | 90.3 FM | Seattle, WA |
| WWOZ | 90.7 FM | New Orleans, LA |
| WFMU | 91.1 FM | Jersey City, NJ |
| WREK | 91.1 FM | Atlanta, GA |
| Ohm Radio | 96.3 FM | Charleston, SC |
| KUTX | 98.9 FM | Austin, TX |
| FIP | 105.1 FM | Paris, France |
| Soho Radio | Online | London, UK |

Footer-only (no embeddable stream, linked out instead): WUTC, WDVX, WPRB, WXYC, WTUL, WUOG.
WXYC/WTUL/WUOG specifically are http-only streams blocked by mixed-content rules on https
pages — see [PLAN.md](PLAN.md) for details.

## Stack

- Single HTML file — no framework, no bundler, no dependencies beyond Google Fonts
- Vanilla JS, ~1150 lines including all station data
- Hosted on GitHub Pages / Cloudflare

## Structure

```
radio/
├── index.html    ← the whole page
├── icons/        ← self-hosted station icons (128×128 PNG, all 15 stations)
├── NOTES.md      ← working notes, stream research, backlog
├── PLAN.md       ← sequenced roadmap
└── README.md     ← this file
```

## Roadmap

See [PLAN.md](PLAN.md) for the sequenced roadmap. High-level:

1. ~~Core page + tuner mechanic~~ ✓
2. ~~Stream verification across all candidate stations~~ ✓
3. ~~Logos + logo-derived accent colors per card~~ ✓
4. ~~Donate links per station~~ ✓
5. ~~Responsive / mobile layout pass~~ ✓
6. Presets / library split, if the roster ever feels crowded in the drum

## Philosophy

Browsing by tuning (drum scroll) rather than search or filter is intentional — it stays
that way even as the list grows. The stations here aren't a comprehensive directory;
they're a personal shortlist that happens to be public.

If a station you love isn't here: it either doesn't have a public stream URL, hasn't
been researched yet, or just hasn't made my personal cut. All three are fine.

## Donating

These stations are listener-supported. If you discover something you love here, please
consider donating directly.

| Station | City | Donate |
|---------|------|--------|
| KZSC | Santa Cruz, CA | [Donate](https://kzsc.org/donate/) |
| WNCW | Spindale, NC | [Donate](https://www.wncw.org/support) |
| The Current | Minneapolis, MN | [Donate](https://www.thecurrent.org/waystogive) |
| WRFG | Atlanta, GA | [Donate](https://wrfg.org/donate/) |
| KCRW | Santa Monica, CA | [Donate](https://join.kcrw.com/) |
| WEVL | Memphis, TN | [Donate](https://wevl.org/pledge) |
| Studio One | Des Moines, IA | [Donate](https://www.studioone.org/support) |
| KEXP | Seattle, WA | [Donate](https://www.kexp.org/donate/) |
| WWOZ | New Orleans, LA | [Donate](https://www.wwoz.org/donate/) |
| WFMU | Jersey City, NJ | [Donate](https://pledge.wfmu.org/donate?step=landing) |
| WREK | Atlanta, GA | [Donate](https://wrekradio.bigcartel.com/product/donation) |
| Ohm Radio 96.3 | Charleston, SC | [Donate](https://www.ohmradio963.org/donate/) |
| KUTX | Austin, TX | [Donate](https://kutx.org/donate/) |
| FIP | Paris, France | — French public broadcasting, no listener-donation model |
| Soho Radio | London, UK | — independent/commercial, no donate page found |

Links verified directly against each station's own site. Same `donateUrl` field
lives in `index.html`'s station data and is wired into each card.

## How this was built

The Dial was built entirely on a phone, through Claude (Sonnet 4.6 and Claude 5 medium effort, on the free tier — which meant the occasional 5-hour token reset, but also meant working on it whenever, in whatever size chunks made sense), without ever opening a laptop.

The starting point was a list of favorite local and regional radio stations. From there the idea took shape in conversation — a rotary drum tuner, real verified stream URLs only, self-hosted logos, pixel-sampled accent colors. Each phase was scoped, built, tested, and committed before moving to the next.

The workflow throughout:

- **Claude read and wrote the repo directly** via a fine-grained GitHub PAT scoped to this repo's contents only. No code was copied and pasted — commits went straight from the conversation to GitHub.
- **Cloudflare Pages was already pointed at the subdomain** before the first line of code, so every push was immediately testable at radio.benneely.com from the same phone being used to build it.
- **Logos came from screenshots** — station Instagram profile photos, app icons, whatever was cleanest. Pasted into chat, processed by Claude (center-crop → circular mask → 128×128px → pixel-sampled accent color), committed to `icons/`.
- **Stream URLs were never guessed** — each one was either found via [deroverda/recommended-radio-streams](https://github.com/deroverda/recommended-radio-streams), extracted from a station's own page, or confirmed live before being added. Stations without a verifiable public URL went to the footer.
- **Testing happened on the actual device** — the same phone used to build it was used to test it, which surfaced real mobile issues (drum arrow tap targets, card scroll behavior on navigation) that would have been invisible on a desktop.

This fits the pattern described in the [App Patterns Field Guide](https://neely.github.io/patterns/) — specifically a read-only variant of Pattern 4 (GitHub as database, fine-grained PAT-gated write, Cloudflare Pages host), with no write path from the browser at all. The repo is the product; the HTML file is the entire app.

## Contributing

Found a broken stream? Know a station that belongs here? Both are welcome:

- **Bug reports** (broken streams, layout issues, anything broken) → [open an issue](https://github.com/neely/radio/issues)
- **Station suggestions** → [open a feature request](https://github.com/neely/radio/issues/new) with the station name, city, and a link to their stream or site

The bar for new stations is the same as the existing roster: a real, public, https-embeddable stream URL, and a format that fits — community, college, independent, public radio.

## License

[MIT](LICENSE) — the code is yours. Streams and station logos belong to their respective stations.
