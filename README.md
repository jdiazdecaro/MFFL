# MFFL — 2026 Dynasty Rookie Draft Grades

Data-driven grades for all 16 teams in the MFFL 2026 rookie draft.

**→ [Draft grades](https://jdiazdecaro.github.io/MFFL/)** · **[Strength of schedule](https://jdiazdecaro.github.io/MFFL/schedule.html)** · **[Trade history](https://jdiazdecaro.github.io/MFFL/trades.html)** · **[The Beat](https://jdiazdecaro.github.io/MFFL/beat.html)** · **[Beat archive](https://jdiazdecaro.github.io/MFFL/beat/)**

## League

| | |
|---|---|
| Format | Dynasty, 2QB / Superflex |
| Teams | 16 |
| Rounds | 5 (linear) |
| Picks | 80 |
| Season | 2026 |

Starting lineup: QB · RB · RB · WR · WR · TE · FLEX · FLEX · SUPERFLEX

## Pages

- **Draft grades** (`index.html`) — all 16 teams graded on the 2026 rookie draft.
- **Strength of schedule** (`schedule.html`) — 14-week schedules ranked easiest to hardest, with an early/late split, each team's toughest matchup, and its worst bye-week collision.
- **Trade history** (`trades.html`) — five seasons of completed trades by calendar month, the two events that drive them, and the in-season week profile.
- **The Beat** (`beat.html`) — a newspaper-style column. The September 17 edition leads with the waiver cycle, Bay Area–CeeDees as matchup of the week, and the injury report. It also covers moves since Monday, Monday’s scoring headline and a second matchup spotlight, then closes with all 16 team storylines. The outgoing September 14 edition is preserved in the archive under [`beat/`](https://jdiazdecaro.github.io/MFFL/beat/).

## Method

### Draft grades

Four inputs, all pulled from the live Sleeper API:

- **Talent** — total value of players acquired, from consensus rank, NFL depth-chart position, and age. Rewards absolute haul, not thrift.
- **Value over slot** — each player's value against what was typically available within eight picks either side. Measures whether a manager beat their own draft position.
- **Impact path** — how many drafted rookies sit at NFL depth-chart 1 or 2, the only ones with a realistic route to 2026 snaps.
- **Need fit** — pre-draft positional shortfall against a superflex lineup.

Talent and value are scored separately on purpose. Collapsing them punishes teams for drafting early with premium picks, which is backwards.

### Strength of schedule

Opponent scores are projected from current rosters, Sleeper's weekly 2026 player projections, and four seasons of measured lineup-setting efficiency per manager. "Toughest week" is the lowest win probability of the season; "bye-week dip" is how far a team's own lineup falls below its average when its starters' NFL byes stack up.

### The Beat

A week-by-week column built from the same live endpoints. Results are actual points scored by the nine
players each manager started, read from this league's own `matchups/{week}` results. Projected scores,
where the page compares against them, are each team's **best legal lineup**
(QB/RB/RB/WR/WR/TE/FLEX/FLEX/SUPERFLEX) scored from **raw projected stats against MFFL's own
`scoring_settings`** — not Sleeper's `pts_ppr`, which ignores this league's completion scoring, rushing
first downs and tight-end premium and misranks QBs and TEs as a result.

An edition published before every NFL game of the week is final says so in its snapshot line, and marks
the teams with players still to play.

`beat.html` is always the current edition, so a link shared with the league keeps working. When a new one
is published the outgoing edition is frozen into `beat/YYYY-MM-DD.html` with a banner marking it as past,
and listed at `beat/index.html`. Archived editions are never rewritten: a number in an old edition is what
was known that morning.

Kick and punt return yards were voted in by the competition committee on 2026-09-11 at 1 point per 20 and
are included throughout. Note that the Sleeper app can display a team total up to 0.02 below the figure
here: this league scores passing yards at 1 point per 30, and the app rounds that down at a different
step. The page uses the league's matchup results, which match a recomputation from raw stats exactly.

Roster value and the under-24 share come from FantasyCalc dynasty values (superflex, full PPR) with a
positional correction for MFFL scoring (QB ×1.14, RB ×1.43, TE ×1.24, WR ×1.00). Pick ownership is read
from `traded_picks`. Every superlative on the page is computed and regression-checked rather than asserted.

No projected records or playoff odds appear on the page — that split is deliberate.

### Trade history

Every `transactions/{week}` endpoint, weeks 1–18, across all five league seasons, filtered to completed trades and deduplicated by transaction ID — 156 in total. Trades are bucketed by `status_updated` (when the trade processed) rather than by league week, so offseason moves land in their true calendar month.

The league was founded 2022-08-16 and the data runs to 2026-08-15, which gives every calendar month exactly 4.0 observed league-months. Raw monthly counts are therefore directly comparable without normalising.

## Caveats

Consensus rank compresses everything outside the top ~250 into a single undifferentiated bucket, so late-round grades separate players by depth chart and age rather than by talent. August depth charts are also noisy and shift through final cuts.

The top of the board is far firmer than the bottom. Value figures are model output, not scouting.

## Source

Built from `api.sleeper.app` draft, roster, user, transaction, and player endpoints. Draft ID `1328167060039020544`, league ID `1328167060034834432`. Trade history additionally uses the 2022–2025 league IDs.
