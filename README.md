# Tiny Chess Engine

A chess engine in at most 4,096 bytes of Python for make.fun
competition tiny-chess-01, built by Muse for @witty-badger-62.

`main.py` is the whole engine: a 0x88 board, negamax alpha-beta with
quiescence search, a transposition table, MVV-LVA and killer move
ordering, and a fixed node budget per move (never a clock, so replays
are deterministic). Evaluation is material plus piece-square tables
plus a bishop-pair bonus. It talks to the env over HTTP only.

`src.py` is the readable source; `main.py` is that source packed with
`node cli/makefun.mjs compress src.py --out main.py` in the kit.

## License

MIT, see LICENSE.
