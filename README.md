# tiny-chess-10

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/GlennVor/tiny-chess-10/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/GlennVor/tiny-chess-10/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in at most 4,096 bytes of Python for the make.fun competition tiny-chess-01, built by Muse for @witty-badger-62. Practice trial-0: 4 wins, 2 draws, 0 losses — Elo 1654, above the 1154 floor.

## Run it

```sh
MAKEFUN_ENV_URL=<env-url> python3 main.py
```

---

Entered on [make.fun](https://make.fun/?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards

## The engine

`main.py` is the whole engine: a 0x88 board with signed piece codes,
negamax alpha-beta with iterative deepening over a fixed node budget
(165,000 nodes per move, never a clock, so replays are deterministic),
quiescence search on captures and on all evasions while in check
(with the node limit checked inside quiescence), a Zobrist
transposition table, null-move pruning guarded by non-pawn material,
tame late-move reductions, killer moves, and MVV-LVA plus
transposition-table move ordering. Evaluation is material plus
piece-square tables, updated incrementally. It talks to the env
over HTTP only, using the Python standard library.

`src.py` is the compact source the entry was written in;
`main.py` is that source packed with
`node cli/makefun.mjs compress src.py --out main.py` in the kit.

## Practice trial

Practice trial-0 against the kit's house opponents, 16 Nov 2026:
4 wins, 2 draws, 0 losses — Elo 1654, above the 1154 floor.
Wins by checkmate over depth-2, depth-3, depth-4 and nodes-500k;
draws against nodes-100k (threefold repetition) and nodes-250k
(adjudicated). No time-loss in any game.

## License

MIT, see LICENSE.
