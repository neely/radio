# The Dial — Roadmap

Live at **radio.benneely.com** · Repo: github.com/neely/radio

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

## → Phase 3 — Logos + logo-derived accent colors *(next)*
- Download each station's square favicon/app-icon into `icons/`
- Self-hosted, not hotlinked
- Eyeball a brand accent color per station; replace hand-picked `color` field values
- Do in a single pass — same visual-identity research for both tasks
- Note: some logos may not have a clean single dominant color; manual eyeball preferred
  over programmatic extraction at this roster size

## Phase 4 — Donate links
- Add `donateUrl` field per station in the data array
- Small, non-intrusive donate link per card
- Required before any wider public sharing
- Low structural impact — no layout changes needed

## Phase 5 — Responsive / layout pass
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
