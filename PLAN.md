# The Dial — Roadmap

Live at **radio.benneely.com** · Repo: github.com/neely/radio

---

## Working conventions
- **Keep README.md in sync.** When a phase here changes data that README surfaces
  (station roster, donate links, stack/structure), update README in the same pass —
  don't let it drift into a stale mirror of index.html. (The "Current stations" table
  went stale twice before this rule stuck — flagged as a TODO on 2026-07-01, still
  hadn't been fixed by 2026-07-03. Actually fixed now; keep it that way.)

---

## ✓ Phase 1 — Core page + tuner mechanic
- Single-file HTML, drum-style rotary tuner, per-card play/pause with VU bars
- Now-playing fetch for stations that expose a public endpoint (silent fallback on failure)
- Footer link-out row for stations without embeddable streams

## ✓ Phase 2 — Stream verification + roster build
- Checked all candidate stations for real, public, https-embeddable stream URLs
- Research reference: **github.com/deroverda/recommended-radio-streams** — invaluable
  directory of verified stream URLs; found The Current, KCRW, Soho Radio, WNCW via this
- Bar: direct confirmation only, no guessed or pattern-matched URLs
- Mixed-content audit: upgraded http→https where possible (WFMU, WWOZ, WEVL, WNCW);
  demoted permanently http-only stations to footer (WXYC, WTUL, WUOG)
- **15 streaming stations** live; 6 footer link-outs; 2 unconfirmed (RTRFM, FBi Radio)

### Stations to test (all confirmed playing as of last check, but verify on each device)
| Station | Stream host | Notes |
|---------|------------|-------|
| OhmRadio 96.3 | Live365 | |
| WNCW 88.7 | audiocdn.com edge | Resurrected from footer |
| KZSC 88.1 | radioca.st | |
| WREK 91.1 | Icecast | Now-playing ✓ |
| WFMU 91.1 | Icecast | https upgraded |
| WWOZ 90.7 | WWOZ.org → StreamGuys | Redirect chain — watch this one |
| WEVL 89.9 | StreamGuys | https upgraded |
| WRFG 89.3 | Radio.co | |
| KUTX 98.9 | KUT/StreamGuys | |
| KEXP 90.3 | StreamGuys | Now-playing ✓ |
| Studio One | Iowa PR | Officially published URL |
| The Current 89.3 | publicradio.org | URL not on MPR's own page |
| FIP | Radio France Icecast | Now-playing attempted, shape unconfirmed |
| KCRW Eclectic24 | streams.kcrw.com | |
| Soho Radio | doughunt.co.uk | Non-standard port 8010 |

## ✓ Phase 3 — Logos + logo-derived accent colors
- All 15 stations have real logos in `icons/` (128×128 PNG, self-hosted) and
  colors sampled from actual logo pixels (no hand-picked/guessed hex values
  remain in the data)
- Actual method differed from the original plan below: Ben uploaded each
  station's logo directly (Instagram profile photos worked best — square,
  clean, high-res) rather than fetching favicons. Turned out favicon fetching
  wasn't viable anyway — no tool available could pull image bytes from an
  external site into the repo, only file uploads from Ben worked.
- Processing pipeline: center-crop → circular alpha mask → resize to 128×128
  → sample accent color from actual pixels (not eyeballed). Several logos
  needed a manual pre-crop first when the badge didn't fill its source frame
  (WTUL, WRFG's first pass, WEVL required a radial color scan to distinguish
  true background from a small inset detail)
- 3 stations (WUOG, WTUL, WXYC) have logos processed and banked in NOTES.md
  but not committed — they're footer-only (see Deferred section below), no
  `id`/`color` field to plug into yet
- KZSC was swapped mid-phase to a more distinctive photo-based badge; WRFG
  was redone once with a higher-res source
- **UI wiring done (2026-07-03):** logo (44px circle) + resized play button
  (also 44px, balanced counterweight) sit in a new logo-row at the top of
  each card. Mocked up 2 layout variants first for review — went with the
  "larger anchor logo" direction over the smaller badge-beside-frequency one.

## ✓ Phase 4 — Donate links
- `donateUrl` added to 13 of 15 stations, verified against each station's own
  site (not a mirror/aggregator)
- FIP and Soho Radio intentionally have no `donateUrl` — FIP is French public
  broadcasting (license-fee funded, no listener-donation model), Soho Radio
  has a merch store but no donate page
- Also added to README's Donating section
- **UI wiring done (2026-07-03):** small text link next to the genre tags,
  only rendered for stations with a `donateUrl`. Click/keydown guarded so it
  doesn't also trigger card selection.

## ✓ Site-wide accent color (2026-07-03)
- `selectStation()` already set `--needle` to the tuned station's color on
  every selection — drives the drum tick, dial-shell border, tuned-station
  name text, dot-wave, and active-card highlight. This was effectively
  "the site reacts to what's playing" already, just waiting on real
  (non-placeholder) colors from Phase 3.
- Considered a full-page background swap to the accent color instead (Ben's
  original idea) but skipped it — several colors in the roster are extreme
  (Soho's near-fluorescent yellow, pure blacks) and a saturated full-bleed
  background would be rough for multi-hour writing-session use. Mocked up
  both options side by side before deciding; kept the cream/paper background
  intact.
- Found a real bug in the process of shipping this: 3 stations (WREK, WWOZ,
  WRFG) have pure black as their color — used raw, that's nearly invisible
  against the drum's dark background, so the tuned station name would go
  nearly unreadable. Added `readoutSafeColor()`, a luminance check that
  lightens any color too close to the dark background's own luminance
  (blends toward paper); the other 12 already-bright colors pass through
  untouched. Verified against all 15 real colors before shipping.

## Phase 5 — Responsive / layout pass *(next)*
- Mobile: drum tuner + card grid not rigorously tested at small widths (eyeballed only)
- Desktop/"at work": more grid columns, wider drum
- Done after logos + donate so card content shape is final before layout is tuned around it

## Phase 6 — Presets / library split *(if needed)*
- Revisit once 15+ stations actually feels crowded in the drum
- Intent: OhmRadio, KEXP, FIP, WFMU as "presets" tier; rest as browsable library
- Simple "add to presets" toggle preferred over drag-and-drop
- Don't build preemptively — wait until the UX problem is actually felt

---

## Stations with unconfirmed streams (need devtools to find URL)
- **RTRFM 92.1** — Perth, Australia. Independent, 400+ volunteers since 1977. Strong fit.
- **FBi Radio 94.5** — Sydney, Australia. Independent, 50% Australian music. Strong fit.

If either stream URL surfaces (someone with devtools inspects their player), add via the
same pattern as the rest of the roster.

## Deferred / won't do
- **WTUL, WUOG, WXYC** — http-only Icecast servers, no TLS, mixed-content blocked on https
  pages. Would need a Cloudflare Worker proxy to fix — out of scope for now.
- **Now-playing for WTUL/WUOG** — Spinitron API requires an auth key from the station.
- **SomaFM** — Network of 30+ channels, intentionally skipped. Worth exploring personally.
- **Drag-to-reorder** — De-scoped. Simple toggle if reordering is ever needed.
- **Roll FM, Clyde 2, Boost Radio** — Not a fit (seasonal/commercial/format mismatch).
