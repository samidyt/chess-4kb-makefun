# chess-4kb-makefun

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/samidyt/chess-4kb-makefun/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/samidyt/chess-4kb-makefun/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 4,069 bytes of Python for the make.fun "strongest chess engine in 4 KB" bounty. The engine is LZMA-compressed inside `main.py` (the rules allow compression); it unpacks into a 0x88-board negamax search with a transposition table, null-move pruning, late-move reductions, killer moves, and a capture quiescence search with check evasions, under a fixed 120,000-node budget per move. Fully deterministic — no clock, no randomness, no model calls.

## Run it

The grader runs `python3 main.py` with `MAKEFUN_ENV_URL` set; the engine plays the house gauntlet through the env (`POST /game`, `POST /move`).

---

<sub>Entered on [make.fun](https://make.fun/?ref=yza5v0ew&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
