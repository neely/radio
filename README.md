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

| Station | Freq | City | Stream |
|---------|------|------|--------|
| KZSC | 88.1 FM | Santa Cruz, CA | ✓ |
| WUOG | 90.5 FM | Athens, GA | ✓ |
| WREK | 91.1 FM | Atlanta, GA | ✓ |
| WFMU | 91.1 FM | Jersey City, NJ | ✓ |
| WTUL | 91.5 FM | New Orleans, LA | ✓ |
| WEVL | 89.9 FM | Memphis, TN | ✓ |
| WXYC | 89.3 FM | Chapel Hill, NC | ✓ |
| WRFG | 89.3 FM | Atlanta, GA | ✓ |
| WWOZ | 90.7 FM | New Orleans, LA | ✓ |
| KUTX | 98.9 FM | Austin, TX | ✓ |
| WREK | 91.1 FM | Atlanta, GA | ✓ |
| KEXP | 90.3 FM | Seattle, WA | ✓ |
| OhmRadio | 96.3 FM | Charleston, SC | ✓ |
| FIP | 105.1 FM | Paris, France | ✓ |

Honorable mentions (no embeddable stream): WNCW, WUTC, WDVX, WPRB, The Current

## Stack

- Single HTML file — no framework, no bundler, no dependencies beyond Google Fonts
- Vanilla JS, ~850 lines including all station data
- Hosted on GitHub Pages / Cloudflare

## Structure

```
radio/
├── index.html    ← the whole page
├── icons/        ← self-hosted station icons (in progress)
├── NOTES.md      ← working notes, stream research, backlog
├── PLAN.md       ← sequenced roadmap
└── README.md     ← this file
```

## Roadmap

See [PLAN.md](PLAN.md) for the sequenced roadmap. High-level:

1. ~~Stream verification across all candidate stations~~ ✓
2. Logos + logo-derived accent colors per card
3. GitHub push + real-device testing (you're here)
4. Presets / library split as roster grows
5. Donate links per station
6. Responsive / mobile + big-screen layout pass

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
now lives in `index.html`'s station data — the on-card donate button is still
pending (see [PLAN.md](PLAN.md)).
