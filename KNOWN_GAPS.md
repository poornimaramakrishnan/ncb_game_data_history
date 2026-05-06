# Known gaps

This dataset is built from ESPN's public scoreboard + summary endpoints. A small
number of games cannot be rendered into XML because ESPN's payload is
malformed or missing critical fields.

| Season  | Game ID    | Issue                                  | Status |
|---------|------------|----------------------------------------|--------|
| 2023-24 | 401602355  | ESPN summary missing `header` block    | Skipped — final 2023-24 count: 6,232 of 6,233 scheduled |

If the UI requests a game that is not present in this repo, it will:

1. Try MotherDuck (`ncb.game_raw.payload_json`)
2. Fall back to a live ESPN API fetch via the Worker proxy

So end users never see a missing game — they just see a slightly slower
single-file download for the few that fall outside the pre-built set.
