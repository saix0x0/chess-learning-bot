# ♞ Pawn Coach — a chess learning bot

A pocket chess coach for beginners, built to take you from "can't get past 300" toward real, durable improvement. You **play**, and a coach watches every move: it names the opening you're in, tells you who's better and what to watch for, and when you slip it shows you the *mistake* and *how to think* — not just the engine's move.

**It runs 100% in your browser.** No accounts, no server, no downloads, no API calls, no tracking. The chess engine, the analysis, and your saved games never leave the page. It's a single HTML file with **zero dependencies** — open `index.html` and play, even offline on a plane.

## What it does

- **Play & coach** — Play a built-in bot (five strength levels, from beatable-beginner to sharp). After every move you get:
  - the **opening / variation** you're in, named live ("Italian Game, Giuoco Piano"…),
  - a plain-English **position assessment** — who's ahead and *why*, your development, whether your king is safe, and **what your opponent is threatening right now**,
  - if you blunder: the mistake, the **better move**, and the **thinking habit** that would have caught it — plus a one-click **"take it back & try again."**
- **Puzzles** — A drill deck built from mini-games, engine-verified tactics, and — the good part — **your own real mistakes** from games you play and import. Every puzzle is correct by construction.
- **Openings by the book** — An interactive opening book that teaches the *idea* behind each move (not 20 moves of memorization), plus a starter repertoire and a dictionary of named openings so you know them all by name.
- **Review a game** — Paste a PGN from chess.com and get a move-by-move coached walkthrough, with your blunders and mistakes marked.
- **Your game** — Behaviour analysis across everything you've played and imported: your top leaks ranked, your style, your castling habit, and the one habit to fix next.
- **How to think** — The mental checklist (What did that move do? Am I safe? Checks-Captures-Threats), how to assess any position, and the classic principles.

## How to use it

1. Open `index.html` in any modern browser. That's it.
2. Start in **Play & coach**. Pick a color and a bot strength and make a move.
3. Lost a piece? Read the coach, hit **take it back**, and play the position better.
4. To feed it your real games: on chess.com open a finished game → **⋯ → Download** (or your profile → Games → Download) to copy the PGN, then paste it in **Review**. Your mistakes flow into **Puzzles** and **Your game** automatically.

Your games and stats are saved in your browser's `localStorage` — private to your device.

## The engine

The chess engine is hand-written and dependency-free. Its move generator passes **perft** exactly on the standard test positions (start position to depth 4 = 197,281; "Kiwipete" to depth 3 = 97,862; the en-passant/promotion position to depth 4 = 43,238), so legality, castling, en passant, promotion, and pin/check handling are provably correct. The coach uses a small alpha-beta search with quiescence, plus a static-exchange evaluation to detect hung pieces and free material the way a beginner should learn to.

It is deliberately **tuned for beginners**: it reliably catches hung pieces, free material, and one-move mates — the mistakes that actually decide games under ~800. It is *not* a 3000-Elo engine and won't find deep 5-move combinations, by design.

## Tech

One file, no build step, no dependencies. Vanilla HTML/CSS/JS. Fonts are the only external resource (Google Fonts); it works fine offline without them.

## License

MIT — see [LICENSE](LICENSE). Do whatever you like with it.
