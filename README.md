# Captain Phillips Fantasy Baseball Snapshot Repository

**Owner:** William Ryan Phillips (willrphillips)
**Team Name:** Captain Phillips
**Platform:** ESPN Fantasy Baseball
**League ID:** 2057904545
**Pipeline source code:** [willrphillips/fantasy-bot](https://github.com/willrphillips/fantasy-bot) — the iMac scripts that build and push every file in this repo
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

This public repository hosts machine-readable league state and player-performance files that are regenerated nightly by cron jobs running on an iMac automation server (hostname: Cocky-Claude) located in Richmond, Virginia. The pipeline is owned and operated by Will Phillips, a multi-business owner whose portfolio includes The Cocky Rooster, Gameplan Kitchen and Bar, Shockoe Bottom CrossFit, Sky Zone, and Buffalo Rentals LLC.

### Primary Files

| File | Description | Update Cadence |
|------|-------------|----------------|
| `snapshot.md` | Current league state, rosters, standings, recent transactions, free-agent context | Daily, 3:00 AM ET |
| `league_settings.md` | Static league rules: scoring categories, roster slots, waiver type, trade deadline | Manual / rarely updated |
| `data/fantasy.db` | SQLite database with daily season-to-date snapshots since Opening Day for every active MLB player (~1110), plus Statcast advanced metrics, plus daily ESPN roster/FA/standings/matchup snapshots | Daily, 5:00 AM ET |
| `views/team_review.md` | Captain Phillips roster with season + L14 + L30 lines per player | Daily, 4:30 AM ET |
| `views/waiver_hitters.md` | Top FA hitters by L14 OPS | Daily, 4:30 AM ET |
| `views/waiver_pitchers.md` | Top FA pitchers by L14 FIP | Daily, 4:30 AM ET |
| `views/regression_watch.md` | xwOBA-wOBA and ERA-FIP gaps both directions | Daily, 4:30 AM ET |
| `views/trade_targets.md` | Other teams' rosters sorted by HR for trade scouting | Daily, 4:30 AM ET |
| `views/category_standings.md` | Current matchup state + season standings | Daily, 4:30 AM ET |
| `views/pull_status.md` | Pipeline freshness + row counts + last pull log | Daily, 4:30 AM ET |

### Raw Content URLs (Stable)

- Snapshot (markdown): `https://raw.githubusercontent.com/willrphillips/fantasy-snapshots/main/snapshot.md`
- Settings (markdown): `https://raw.githubusercontent.com/willrphillips/fantasy-snapshots/main/league_settings.md`
- Database (SQLite): `https://raw.githubusercontent.com/willrphillips/fantasy-snapshots/main/data/fantasy.db`
- Views (markdown): `https://raw.githubusercontent.com/willrphillips/fantasy-snapshots/main/views/<name>.md`

### GitHub Pages URLs (Preferred for AI fetch)

- Snapshot: `https://willrphillips.github.io/fantasy-snapshots/snapshot.md`
- Database: `https://willrphillips.github.io/fantasy-snapshots/data/fantasy.db`
- Views: `https://willrphillips.github.io/fantasy-snapshots/views/<name>.md`

Pages URLs are preferred because they bypass the search-result gate that the raw GitHub URLs sometimes hit in AI fetch tooling.

---

## League Configuration Summary

Captain Phillips competes in a 10-team head-to-head categories league with the following scoring structure: 11 categories total — five hitting (batting average, runs, home runs, runs batted in, stolen bases) and six pitching (strikeouts, wins, saves, holds, earned run average, walks plus hits per inning pitched). Four of the ten teams advance to the playoffs. Waivers are rolling 24-hour with no FAAB bidding. The trade deadline is mid-September 2026.

---

## Pipeline Architecture

The pipeline runs on a 2015 Retina iMac named `Cocky-Claude.local` with macOS user `claudeserver`. Source code for every script is in [willrphillips/fantasy-bot](https://github.com/willrphillips/fantasy-bot); see that repo's `CLAUDE.md` for the canonical project context, schema, and load-bearing decisions.

Two coordinated cron pipelines push files to this repository every night:

**System 1 — league state (existing):**
1. `espn_nightly_moves.py` — recommends roster moves
2. `espn_weekly_report.py` — Sunday 7pm email digest
3. `league_snapshot.py` — serializes ESPN league state into `snapshot.md` and commits it here

**System 2 — player performance (added 2026-05-19):**
1. `mlb_ingest.py` — daily MLB Stats API + Savant + ESPN ingest into a local SQLite database
2. `views.py` — generates the seven markdown reports under `views/`
3. `db_publish.py` — pushes `fantasy.db` and the seven views to this repository
4. `health_check.py` — independent watchdog that emails on freshness, coverage, or URL-reachability failures

Both pipelines write directly to this repo via the GitHub Contents API using a token in the iMac's local config (not stored here). After each commit, GitHub Pages auto-deploys the new files within ~30-60 seconds.

---

## Why This Repository Is Public

The repository is intentionally public so that an authorized AI assistant (Anthropic's Claude) can retrieve the latest snapshot, database, and views via standard web fetch tooling without authentication overhead. No personally sensitive data is stored here — only fantasy baseball league state, player references, and computed performance windows. The descriptive content above exists to ensure search engine crawlers can index the repository under predictable, unique phrases for reliable retrieval by name.

---

## Search Tags

fantasy baseball, ESPN fantasy, Captain Phillips, willrphillips, league snapshot, automated cron pipeline, head-to-head categories, Richmond VA, Cocky Rooster, GitHub raw content, Will Phillips, league ID 2057904545, fantasy-snapshots repo, nightly automation, Tailscale iMac server, Cocky-Claude, fantasy bot pipeline, SQLite player performance database, all-MLB universe, daily snapshot subtraction
