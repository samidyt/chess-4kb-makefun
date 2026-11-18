# chess-4kb-makefun

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/samidyt/chess-4kb-makefun/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/samidyt/chess-4kb-makefun/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 3,981 bytes of Python for the make.fun "strongest chess engine in 4 KB" bounty. The engine is LZMA-compressed inside `main.py` (the rules allow compression); it unpacks into a 0x88-board negamax search with a transposition table, null-move pruning, late-move reductions, killer moves, and a capture quiescence search with check evasions, under a fixed 120,000-node budget per move. v1.5 adds repetition awareness (the search scores repeated positions as draws, so the engine converts winning positions instead of repeating into draws) and underpromotions in search. Fully deterministic — no clock, no randomness, no model calls.

## v1.5

v1.5 keeps v1's evaluation and search untouched and adds two targeted
fixes: the search now treats repeated positions as draws (v1 drew two
winnable games by threefold repetition), and move generation covers
all four promotion pieces instead of queen-only. Practice trials:
trial-0 Elo 1,545 (4W 1D 1L), trial-1 Elo 1,451 (3W 2D 1L), mean
1,498 vs v1's 1,467 — stronger on average and steadier across trials
(range 94 Elo vs v1's 375). The repetition fix turned the game-4
draw into a win in each trial.

v1.5r replaces the repetition check's list scan with a set lookup.
It plays identically to v1.5 — same moves on 10/10 test positions,
identical node counts — so the change is speed only. main.py is now
3,981/4,096 bytes.

An earlier v2 (PeSTO tapered eval + PVS) scored worse in trials
(mean 1,412) and was dropped; the eval swap is the likeliest
cause of the regression, though unproven.

## Run it

The grader runs `python3 main.py` with `MAKEFUN_ENV_URL` set; the engine plays the house gauntlet through the env (`POST /game`, `POST /move`).

---

<sub>Entered on [make.fun](https://make.fun/?ref=svtazsn5&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
