---
name: follow-matches-and-tables
description: Live football scores, results, fixtures, match centres, league tables and FootVal's daily match predictions — today's games, a team's next or last matches, one match's event timeline, statistics and line-ups, the current standings, and the model's calls for the day with its track record. Use for "what's the score", "who plays tonight", "when is Galatasaray's next game", "show me the Süper Lig table", "how did yesterday's Champions League games go", "what does FootVal predict today".
---

# Scores, matches and tables

## Which tool

- Several matches → `get_matches` with `when` = `live`, `today`, `yesterday`, `tomorrow` or a
  `YYYY-MM-DD` date, optionally narrowed by `competition` or `team`.
- One match in depth → `get_match` with a `match_id` from `get_matches` or `get_team_fixtures`.
- One team's schedule → `get_team_fixtures` (`direction`: `next` or `last`, `count` 1–10; set
  `national: true` when a national team shares its name with a club).
- A table → `get_standings` (current season by default; `season` is the start year).
- FootVal's predictions → `get_predictions` (`day`: `today`, `yesterday` or a `YYYY-MM-DD`
  date; `team` keeps only that team's matches).

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

## Predictions

- Every morning before the first kick-off FootVal's statistical model locks in its 10 most
  confident calls of the day (match result, double chance, total goals or both teams to score)
  and grades each one after the final whistle. Only those calls exist — there is no prediction
  for every match, so don't invent one for a match that isn't on the list.
- A prediction day runs 09:00 → 09:00 UTC, so a late match can belong to the previous day's list.
- Quote the model's probability as a probability ("the model gives it 85 %"), never as a
  certainty, and give the running hit rate alongside. FootVal shows no odds and gives no betting
  advice — don't present a call as a bet.
- A call still being played carries the live score and whether it is on course; for an update,
  call again.
