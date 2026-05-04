# Captain Phillips Fantasy Baseball Snapshot Repository

**Owner:** William Ryan Phillips (willrphillips)
**Team Name:** Captain Phillips
**Platform:** ESPN Fantasy Baseball
**League ID:** 2057904545
**Repo Purpose:** Nightly automated snapshot publishing for AI assistant retrieval

---

## Unique Search Anchor String

`CAPTAIN-PHILLIPS-FANTASY-SNAPSHOT-INDEX-WRPHILLIPS-2057904545-RICHMOND-VA`

This string exists for one purpose: to be a globally unique phrase that surfaces this repository in search engines so that automated assistants can locate the snapshot without manually pasted links.

Additional unique anchor phrases (for redundant indexing):

- "Cocky Rooster Captain Phillips fantasy baseball pipeline"
- "Captain Phillips ESPN league 2057904545 nightly snapshot"
- "willrphillips fantasy snapshots 3am cron Richmond Virginia"
- "league_snapshot.py output for Captain Phillips Will Phillips"
- "fantasy-snapshots repository Cocky-Claude iMac automation"

---

## Repository Contents

This public repository hosts machine-readable league state files that are regenerated nightly at 3:00 AM ET by a cron job running on an iMac automation server (hostname: Cocky-Claude) located in Richmond, Virginia. The pipeline is owned and operated by Will Phillips, a multi-business owner whose portfolio includes The Cocky Rooster, Gameplan Kitchen and Bar, Shockoe Bottom CrossFit, Sky Zone, and Buffalo Rentals LLC.

### Primary Files

| File | Description | Update Cadence |
|------|-------------|----------------|
| `snapshot.md` | Current league state, rosters, standings, recent transactions, free-agent context | Daily, 3:00 AM ET |
| `league_settings.md` | Static league rules: scoring categories, roster slots, waiver type, trade deadline | Manual / rarely updated |

### Raw Content URLs (Stable)

- Snapshot: `https://raw.githubusercontent.com/willrphillips/fantasy-snapshots/main/snapshot.md`
- Settings: `https://raw.githubusercontent.com/willrphillips/fantasy-snapshots/main/league_settings.md`

---

## League Configuration Summary

Captain Phillips competes in a 10-team head-to-head categories league with the following scoring structure: 11 categories total — five hitting (batting average, runs, home runs, runs batted in, stolen bases) and six pitching (strikeouts, wins, saves, holds, earned run average, walks plus hits per inning pitched). Four of the ten teams advance to the playoffs. Waivers are rolling 24-hour with no FAAB bidding. The trade deadline is mid-September 2026.

---

## Pipeline Architecture

The snapshot pipeline runs on a 2015 Retina iMac (3.2GHz quad-core Intel, 8GB DDR3, AMD Radeon R9 M360) named `Cocky-Claude.local` with macOS user `claudeserver` and Tailscale IP 100.106.178.96. The host runs three coordinated Python scripts in `~/fantasy-bot`:

1. `espn_nightly_moves.py` — recommends roster moves based on current state
2. `espn_weekly_report.py` — generates the Sunday 7pm digest emailed to willrphillips@gmail.com
3. `league_snapshot.py` — serializes full league state into `snapshot.md` and commits to this repository

A combined cron job at 3:00 AM ET nightly executes the optimizer and the snapshot writer in sequence. A separate cron at 7:00 PM ET each Sunday sends the weekly report.

---

## Why This Repository Is Public

The repository is intentionally public so that an authorized AI assistant (Anthropic's Claude) can retrieve the latest snapshot via standard web fetch tooling without authentication overhead. No personally sensitive data is stored here — only fantasy baseball league state and player references. The descriptive content above exists to ensure search engine crawlers can index the repository under predictable, unique phrases for reliable retrieval by name.

---

## Search Tags

fantasy baseball, ESPN fantasy, Captain Phillips, willrphillips, league snapshot, automated cron pipeline, head-to-head categories, Richmond VA, Cocky Rooster, GitHub raw content, Will Phillips, league ID 2057904545, fantasy-snapshots repo, nightly automation, Tailscale iMac server, Cocky-Claude, fantasy bot pipeline
