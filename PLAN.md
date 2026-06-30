# The Dial — Roadmap

Sequenced plan. Each phase unblocks the next.

---

## ✓ Phase 1 — Core page + tuner mechanic
- Single-file HTML player with drum-style rotary tuner
- Per-card play/pause with animated VU bars and live status
- Now-playing metadata fetch where stations expose a public endpoint
- Footer link-out row for stations without embeddable streams
- Station data: 13 streamable stations, 5 honorable-mention link-outs

## ✓ Phase 2 — Stream verification across all candidates
- Checked all 11 backlog stations for real, public, embeddable stream URLs
- 8 confirmed and added to the page; 3 moved to footer link-outs
- Documented research approach, stream URLs, and now-playing notes in NOTES.md
- Bar established: no guessed or pattern-matched URLs — direct confirmation only

## → Phase 3 — Logos + logo-derived accent colors *(next)*
- Download each station's square favicon/app-icon into `icons/`
- Self-hosted (not hotlinked) for durability
- Eyeball a brand accent color per station from their real visual identity
- Replace current hand-picked `color` field values with logo-grounded ones
- Both tasks done in a single pass — same stations, same visual-identity research
- Note: some stations may not have a clean single dominant color; manual eyeball
  is more reliable than programmatic extraction at this roster size

## Phase 4 — Real-device testing
- Push to radio.benneely.com via GitHub (Cloudflare-handled)
- Test all 13 streams from phone
- Watch for: mixed-content blocking on `http://` stream URLs (WFMU, WXYC, WWOZ,
  WTUL, WUOG may be affected if the page is served over HTTPS)
- Confirm now-playing appears for KEXP (high confidence), WREK/KZSC (medium),
  WFMU/WXYC (unverified endpoint), FIP (endpoint real, shape unconfirmed)

## Phase 5 — Donate links
- Add `donateUrl` field per station in the data array
- Small donate link/button per card (non-intrusive, below genre tags)
- Must be in place before any wider public sharing of the page
- Low-effort, no structural changes needed

## Phase 6 — Presets / library split
- Revisit once the full roster is live and actually feels crowded in the drum
- Current intent: top personal picks (at minimum OhmRadio, KEXP, FIP, WFMU)
  become a "presets" tier; rest become a browsable library section
- Reordering: a simple "add to presets" toggle preferred over drag-and-drop
- Don't build this preemptively — wait until the UX problem is actually felt

## Phase 7 — Responsive pass
- Deliberate mobile-friendly layout pass (drum tuner + cards not rigorously
  tested at small widths — eyeballed only)
- Big-screen / "at work" layout consideration: more grid columns, wider drum
- Done last so card content (logos, donate links) is final before layout is tuned
- radio.benneely.com is the test target throughout

---

## Deferred / won't do (for now)

- **Now-playing for WTUL/WUOG via Spinitron**: their API requires an auth key
  issued by each station, out of scope. Spinitron's public iframe widget is an
  option but needs its own design work to fit the card layout.
- **WDVX, WPRB, The Current**: stream URL not publicly findable without browser
  devtools inspection on a live session. Not pursuing further — they live as
  footer link-outs. Would revisit only if someone provides a verified stream URL.
- **Drag-to-reorder**: explicitly de-scoped. Not worth the complexity at this stage.
- **Tryzub Radio**: not a music station — it's an X/Twitter Space discussion format,
  no audio stream at all. Not a fit for this project.
