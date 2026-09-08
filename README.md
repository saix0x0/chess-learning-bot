# ♞ Pawn Coach — a chess learning bot

A pocket chess coach for beginners, built to take you from "can't get past 300" toward real, durable improvement. You **play**, and a coach watches every move: it names the opening you're in, tells you who's better and what to watch for, and when you slip it shows you the *mistake* and *how to think* — not just the engine's move.

**It runs 100% in your browser.** No accounts, no server, no downloads, no API calls, no tracking. The chess engine, the analysis, and your saved games never leave the page. It's a single HTML file with **zero dependencies** — open `index.html` and play, even offline on a plane.

## What it does

- **Play & coach** — Play a built-in bot (six strength levels, from beatable-beginner to a depth-4 search that finds forced mates). The point is to change how you *think*, not to do the thinking for you:
  - **Blunder-check (decision gate):** the moment before you play a blunder or a mistake, the coach stops you and asks a *question* — "count the attackers and defenders on that square", "look at your king" — without revealing the move. You either spot it yourself and play something better (logged as a *catch*), or push it through (logged as an *override*).
  - **Tiered hint:** the 💡 gives a category nudge first, then the area, and only then the move — so you still do the work.
  - **A personal, evolving rulebook:** every move is logged (what you played, the verdict, how long you took, which enemy piece punished you, whether it was a fork). Those patterns become a short, ranked checklist of *your* rules — "Slow down, you blunder when you rush", "Watch for enemy knight forks" — shown right next to the board and in **Your game**, updating as your mistakes change.

  On top of that, after each move you still get:
  - the **opening / variation** you're in, named live ("Italian Game, Giuoco Piano"…),
  - a plain-English **position assessment** — who's ahead and *why*, your development, whether your king is safe, and **what your opponent is threatening right now**,
  - a **"your move" tip** telling you what to think about next (castle now, grab the free piece, meet the threat…),
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

## Sync across your devices

Open the **published version** on your Claude account (phone *and* laptop) and your games, puzzle progress, and stats **sync automatically** across them — powered by the artifact's private per-account storage, still with no API keys and no third-party service. A small badge in the corner shows `☁ synced` when it's on, or `● this device` when you're running the raw file offline.

When you open `index.html` directly (offline, or from this repo), everything still works and saves to your browser's `localStorage` — private to that device.

## The engine

The chess engine is hand-written and dependency-free. Its move generator passes **perft** exactly on the standard test positions (start position to depth 4 = 197,281; "Kiwipete" to depth 3 = 97,862; the en-passant/promotion position to depth 4 = 43,238), so legality, castling, en passant, promotion, and pin/check handling are provably correct. The coach uses a small alpha-beta search with quiescence, plus a static-exchange evaluation to detect hung pieces and free material the way a beginner should learn to.

It is deliberately **tuned for beginners**: it reliably catches hung pieces, free material, and one-move mates — the mistakes that actually decide games under ~800. It is *not* a 3000-Elo engine and won't find deep 5-move combinations, by design.

## Tech

One file, no build step, no dependencies. Vanilla HTML/CSS/JS. Fonts are the only external resource (Google Fonts); it works fine offline without them.

## License

MIT — see [LICENSE](LICENSE). Do whatever you like with it.
