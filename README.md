# SOLMAR-4K — tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/cassian27/make-fun-tiny-chess-01-solmar-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/cassian27/make-fun-tiny-chess-01-solmar-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A pure-Python chess engine in at most 4,096 bytes for
[make.fun's tiny-chess-01](https://make.fun/bounty/tiny-chess-01) bounty:
the strongest chess engine you can write in 4 KB of Python.

`main.py` is the whole engine: negamax alpha-beta with quiescence,
transposition table, MVV-LVA and killer ordering, null-move pruning,
late-move reductions, and a material + piece-square + bishop-pair +
passed-pawn evaluation. It searches to a fixed node budget per move
(150,000 nodes), never a clock and with no unseeded randomness, so a
trial's replay plays the same moves. Python 3.13, standard library only.

It plays the house gauntlet through the env at `MAKEFUN_ENV_URL`:
POST `/game` serves the game in play, POST `/move` plays a move.

## The size rule

- `main.py` is the whole engine: at most 4,096 bytes as committed.
  The readable source is packed with the kit's `makefun compress`
  (LZMA payload + unpacker); the packed file is what is committed.
- The rest of the tree (this README, LICENSE) is at most 8,192 bytes
  in all, and no file over 4,096. MIT licence.

## Grade it locally

Download the competition's dev kit, unpack it, and from inside it run:

    makefun grade-local --kit . --bot <your repository> --driver docker

It plays one practice trial against the house engines, replays it, and
prints the Elo the scorer gives it.
