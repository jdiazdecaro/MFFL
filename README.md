# MFFL — 2026 Dynasty Rookie Draft Grades

Data-driven grades for all 16 teams in the MFFL 2026 rookie draft.

**→ [View the grades](https://jdiazdecaro.github.io/MFFL/)**

## League

| | |
|---|---|
| Format | Dynasty, 2QB / Superflex |
| Teams | 16 |
| Rounds | 5 (linear) |
| Picks | 80 |
| Season | 2026 |

Starting lineup: QB · RB · RB · WR · WR · TE · FLEX · FLEX · SUPERFLEX

## Method

Grades combine four inputs, all pulled from the live Sleeper API:

- **Talent** — total value of players acquired, from consensus rank, NFL depth-chart position, and age. Rewards absolute haul, not thrift.
- **Value over slot** — each player's value against what was typically available within eight picks either side. Measures whether a manager beat their own draft position.
- **Impact path** — how many drafted rookies sit at NFL depth-chart 1 or 2, the only ones with a realistic route to 2026 snaps.
- **Need fit** — pre-draft positional shortfall against a superflex lineup.

Talent and value are scored separately on purpose. Collapsing them punishes teams for drafting early with premium picks, which is backwards.

## Caveats

Consensus rank compresses everything outside the top ~250 into a single undifferentiated bucket, so late-round grades separate players by depth chart and age rather than by talent. August depth charts are also noisy and shift through final cuts.

The top of the board is far firmer than the bottom. Value figures are model output, not scouting.

## Source

Built from `api.sleeper.app` draft, roster, user, and player endpoints. Draft ID `1328167060039020544`, league ID `1328167060034834432`.
