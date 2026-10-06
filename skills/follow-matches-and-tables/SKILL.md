---
name: follow-matches-and-tables
description: Live football scores, results, fixtures, match centres and league tables through FootVal — today's games, a team's next or last matches, one match's event timeline, statistics and line-ups, and the current standings. Use for "what's the score", "who plays tonight", "when is Galatasaray's next game", "show me the Süper Lig table", "how did yesterday's Champions League games go".
---

# Scores, matches and tables

## Which tool

- Several matches → `get_matches` with `when` = `live`, `today`, `yesterday`, `tomorrow` or a
  `YYYY-MM-DD` date, optionally narrowed by `competition` or `team`.
- One match in depth → `get_match` with a `match_id` from `get_matches` or `get_team_fixtures`.
- One team's schedule → `get_team_fixtures` (`direction`: `next` or `last`, `count` 1–10; set
  `national: true` when a national team shares its name with a club).
- A table → `get_standings` (current season by default; `season` is the start year).

Full argument list:
[`../value-and-compare-players/references/tools.md`](../value-and-compare-players/references/tools.md).

## Time and dates

- `when` dates are **UTC days**. A late-evening kick-off in the Americas can fall on the next UTC
  day — if a match seems missing, check the adjacent day.
- Kick-off times are UTC timestamps. Convert them to the user's time zone when you know it and
  name the zone you used.

## Live data

- A score is live at the moment of the call. Never extrapolate or invent a score, scorer or
  minute; for an update, call again.
- A match that hasn't started has no events yet, and line-ups only appear shortly before
  kick-off.
- xG and some team statistics are not available for every competition — leave them out rather
  than estimating.

## Tables

- Qualification and relegation zones come with the table, along with each team's recent form.
- Some competitions return more than one table (groups) — present the one the user asked about.
