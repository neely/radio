# The Dial — backlog / notes

## Current streaming stations (live in index.html — 15 total)
- OhmRadio 96.3 — Charleston, SC (Live365)
- WNCW 88.7 — Spindale, NC (audiocdn.com edge AAC — resurrected from footer after https stream found)
- KZSC 88.1 — Santa Cruz, CA (Icecast/radioca.st, now-playing attempted)
- WREK 91.1 — Atlanta, GA (Icecast, now-playing confirmed working)
- WFMU 91.1 — Jersey City, NJ (Icecast, now-playing attempted)
- WWOZ 90.7 — New Orleans, LA (WWOZ.org redirect → StreamGuys)
- WEVL 89.9 — Memphis, TN (StreamGuys)
- WRFG 89.3 — Atlanta, GA (Radio.co)
- KUTX 98.9 — Austin, TX (KUT/StreamGuys)
- KEXP 90.3 — Seattle, WA (StreamGuys AAC, now-playing confirmed working via api.kexp.org)
- Studio One — Des Moines, IA (Iowa Public Radio, officially published URL)
- The Current 89.3 — Minneapolis, MN (publicradio.org — found via deroverda directory, MPR's own streams page only shows a JS player)
- FIP — Paris, France (Radio France Icecast, now-playing attempted, exact JSON shape unconfirmed)
- KCRW Eclectic24 — Santa Monica, CA (streams.kcrw.com)
- Soho Radio — London, UK (Online-only, no FM frequency)

## Footer link-outs (no embeddable stream)
- WUTC 88.1 — Chattanooga, TN (NPR Brightspot CMS)
- WDVX — Knoxville, TN (StreamGuys, URL buried in JS player)
- WPRB — Princeton, NJ (Radio Rethink JS player)
- WXYC 89.3 — Chapel Hill, NC (http-only ibiblio Icecast, mixed-content blocked)
- WTUL 91.5 — New Orleans, LA (http-only raw IP Icecast, mixed-content blocked)
- WUOG 90.5 — Athens, GA (http-only Icecast, mixed-content blocked)

Note: WNCW previously had no public stream; an https CDN URL was found via the
deroverda/recommended-radio-streams directory and it was resurrected into the grid.
WUTC remains footer-only — its NPR Brightspot limitation is permanent.

## Not a fit for this project
- **Tryzub Radio** — Not a music station; "Listen Now" links to an X/Twitter Space.
- **Roll FM** (Finland) — Seasonal broadcaster (~2-month runs), http-only stream.
- **Clyde 2** (Scotland) — Rebranded as "Greatest Hits Radio Glasgow & West", now a
  commercial Bauer Media oldies station. Doesn't fit the roster ethos.
- **Boost Radio** — Commercial pop/hip-hop/EDM, not a fit.
- **SomaFM** — Commercial-free internet network with 30+ channels; intentionally
  skipped — it's a network, not a station. Worth exploring personally.

## Stream URL unconfirmed — devtools needed
These have real public streams but URLs are buried in JS players:
- **RTRFM 92.1** — Perth, Australia. Independent, 400+ volunteers, 50+ programs since
  1977. Strong fit; just needs a URL. Homepage: rtrfm.com.au
- **FBi Radio 94.5** — Sydney, Australia. Independent non-profit, 50% Australian music.
  Same situation. Homepage: fbi.radio

## Useful reference
The deroverda/recommended-radio-streams GitHub directory is the best single resource
for verified stream URLs found so far — confirmed The Current, KCRW, Soho Radio, WFMU,
WXYC, WNCW URLs in one pass. Worth checking first before any future station research.

## Candidate stations to add (not yet in the page)
Stream verification pass completed 2026-06-30 — all 9 remaining backlog
stations checked (KEXP and FIP already graduated to the live page earlier).
Bar is the same as the rest of the roster: a real, public, embeddable stream
URL — no guessing, no pattern-matching from other stations' URLs. Results
below; nothing has been added to index.html yet, this is research only
pending the logo/color pass.

### Confirmed — real direct stream URL found
- **WFMU** — Jersey City, NJ. `http://stream0.wfmu.org/freeform-128k-primary.mp3`
  (raw Icecast, confirmed live with 539 listeners at check time, "Currently
  playing" populated). Status-json equivalent should exist at
  `stream0.wfmu.org/status-json.xsl` for now-playing, same pattern as WREK.
- **WWOZ** — New Orleans, LA. `http://wwoz-sc.streamguys.com/wwoz-hi.mp3`
  (StreamGuys-hosted, well-documented across multiple independent sources/years).
  Correct frequency is 90.7, not 88.1 as originally logged.
- **WXYC** — Chapel Hill, NC. `http://audio-mp3.ibiblio.org:8000/wxyc.mp3` (raw
  Icecast on ibiblio, confirmed live with 32 listeners at check time). First
  station in the world to webcast (1994).
- **KUTX** — Austin, TX. `https://streams.kut.org/4428_192.mp3?aw_0_1st.playerid=kutx-free`
  (officially published by KUT/KUTX, explicitly the current post-migration URL
  as of an April 2024 platform change — not a stale legacy link).
- **WRFG** — Atlanta, GA. `https://s2.radio.co/s2133c4bad/listen` (Radio.co-hosted,
  confirmed via literal `<audio src>` on a third-party player page).
- **WTUL** — New Orleans, LA. `http://129.81.255.83:8000/stream` (raw IP-based
  Icecast/Shoutcast, published directly on the station's own stream page as an
  m3u link). Uses Spinitron for playlists — see now-playing note below.
- **WUOG** — Athens, GA. `http://stream.wuog.org:8000/stream` (explicitly
  published by the station itself as "a direct stream link" on their live-stream
  page). Also uses Spinitron — see now-playing note below.
- **WEVL** — Memphis, TN. `http://wevl.streamguys1.com/live` (StreamGuys-hosted,
  independently confirmed via a personal radio-streaming reference page, not
  guessed from the WDVX pattern below — this one's slug is directly verified).

### Not confirmed — no public stream URL found, do not guess
- **WDVX** — Knoxville, TN. Runs on StreamGuys (`player.streamguys.com/wdvx/...`)
  like several confirmed stations, but the actual audio URL is loaded dynamically
  by the player's JS and wasn't visible in static HTML. Did not guess a
  `wdvx.streamguys1.com/...`-style URL by pattern-matching other StreamGuys
  stations — that would be an unverified assumption. Would need direct browser
  devtools inspection (Network tab) to get the real URL.
- **WPRB** — Princeton, NJ. Runs on a third-party platform called "Radio Rethink"
  (radiorethink.com), same JS-wrapper pattern as NPR Brightspot — no plain stream
  URL in static HTML. A test fetch of the player page returned "Cannot Connect,"
  though that may just reflect the fetch not being a real browser session rather
  than the stream actually being down.
- **The Current** — Minneapolis, MN (MPR/Minnesota Public Radio). Same
  JS-player-wrapper pattern as MPR's other services — no plain stream URL
  surfaced anywhere, including on their own dedicated `/streams` page. Same
  treatment as WNCW/WUTC: this is a major station that clearly wants listeners
  using their official app/player, not a small independent station that simply
  hasn't published one. Recommend treating as link-out-only like WNCW/WUTC if
  added at all, not chasing further.

### Now-playing notes for the confirmed batch
- WFMU and WXYC are both raw Icecast — likely have a `status-json.xsl` endpoint
  the same way WREK and KZSC do. Not yet verified directly, would need a quick
  check when actually wiring these in.
- WTUL and WUOG both use **Spinitron** for playlists/now-playing. Spinitron's
  full JSON API requires an authenticated API key (their terms of service
  explicitly prohibit anonymous/unauthenticated use) — not something wireable
  without the station issuing Benjamin a personal key, out of scope for now.
  However, Spinitron also offers a public, no-auth **iframe widget**
  (`widgets.spinitron.com/widget/now-playing-v2?station=<slug>`) that could
  show now-playing for these two — different mechanism than the fetch-based
  approach used elsewhere (an iframe embed, not a JSON parse), would need its
  own small amount of design work to fit the card layout.
- KUTX, WRFG, WWOZ: no now-playing endpoint surfaced during this pass. Not
  pursued further since stream confirmation was the priority this round.

### Already on the page (not candidates anymore)
KEXP and FIP were originally on this backlog list but have since been added to
the live page — see "Current presets" above.

Useful for future research: a curated GitHub directory exists specifically for
this kind of stream-hunting — github.com/deroverda/recommended-radio-streams —
already used successfully this round for WFMU and WXYC.

When actually adding a confirmed station to index.html, repeat the pattern used
for the existing roster:
1. Stream URL — already done for the 7 confirmed above.
2. Now-playing endpoint if one exists, written defensively with silent fallback
   on parse failure (see FIP's parser as the template for "endpoint is real but
   exact shape isn't confirmed").
3. City/state, one-line description, 2-3 genre tags.
4. Square icon (favicon/app-icon) — part of the upcoming logo pass, not done yet.

## Open structural decisions (deferred, not yet built)
- **Presets vs. library split.** As the station count grows past ~10-12, the
  original 5 (Benjamin's actual favorites, esp. OhmRadio/Charleston) likely become
  a curated "presets" tier, with the rest in a separate browsable library section.
  Not built yet — current list is flat. Revisit once the list actually feels
  crowded.
- **Reordering/ranking.** Explicitly de-scoped — not drag-and-drop. If revisited,
  a simpler "add to presets" toggle (order = whenever added) was the fallback
  option preferred over full drag-and-drop.
- **Logos.** Decided: self-hosted in the repo (not hotlinked), for durability.
  Not yet built. Recommended approach when picked up: use each station's small
  square favicon/app-icon rather than their full marketing logo — these are
  closer to "meant for third-party display" than a full logo mark, lower
  licensing risk, and read fine at card-size. Worth a quick licensing gut-check
  per station before publishing publicly regardless.
- **Logo-derived accent colors.** Raised 2026-06-30: instead of (or alongside) the
  current hand-picked per-station accent colors (`color` field — orange/teal/rust
  reused across stations somewhat arbitrarily), consider pulling each station's
  actual brand color from their real logo/site to drive the active-card and
  "live" accent. Not decided how — could be a manually eyeballed hex per station
  (simple, reliable) or programmatic extraction from the downloaded logo file
  (more automatic, but real logos are often multi-color, black/white-only, or
  lack one clean dominant color, so this may need a manual fallback anyway).
  Natural to do in the same pass as the Logos work above, since both involve
  looking closely at each station's actual visual identity.
- **Donate links.** Data done 2026-07-01 — `donateUrl` added to 13 of 15 stations,
  each verified against the station's own site (not a mirror/aggregator) this
  session. FIP and Soho Radio intentionally have no `donateUrl`: FIP is French
  public broadcasting funded via license fee/Radio France, no listener-donation
  model exists; Soho Radio is independent/commercial-adjacent with a merch store
  but no donate page found. UI (link/button on the card) still not wired in —
  that's the remaining piece before this phase is closed out.
- **Responsive design pass.** Before public release: a deliberate mobile-friendly
  layout pass (drum tuner + cards eyeballed but not rigorously tested at small
  widths) and a separate "at work / big screen" layout consideration — likely more
  columns in the grid and a wider drum, rather than just stretching the mobile
  layout. Deliberately sequenced *after* logos/now-playing settle, so the card
  content shape is final before tuning layout around it.

## Known permanent limitations (not bugs)
- WNCW and WUTC cannot be embedded — NPR's Brightspot CMS doesn't expose a public
  stream URL outside its own JS player. They live as small text links in the
  footer, not as playable cards. This is expected behavior, not a defect.
- FIP's now-playing parser is written defensively (tries a few plausible JSON key
  paths, returns null on any mismatch) because the exact response shape of
  radiofrance.fr/fip/api/live wasn't independently confirmed — only that the
  endpoint itself is real and actively used by others. If it never shows a track,
  that's the most likely reason; worth revisiting by actually inspecting a live
  response.
- The "browse by tuning" interaction (drum scroll instead of e.g. search/filter) is
  intentional even as the station count grows — flagged by Benjamin as a feature,
  not a discoverability bug, at least for now.
