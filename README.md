# Killer Darts Scorer

A single-page, phone-first scorer for the darts game **Killer**. You just tap what was
thrown (single/double/triple + number) and the app derives lives and killer status from
the log — no manual score-fiddling.

## Rules it implements

- Each player claims a number (1–20).
- Hitting your own number scores points toward becoming a killer: single = 1, double = 2,
  triple = 3. You become a killer once you've accumulated **3 points** (fixed, regardless
  of starting lives).
- Once you're a killer, hitting an opponent's number costs them lives equal to the
  multiplier (single −1, double −2, triple −3).
- By default, a killer hitting their **own** number does nothing further. Turning on
  **hard mode** makes self-hits cost lives too, on the same scale.
- Optional **doggy life** rule: reaching 0 lives is safe, but the first time a player
  would drop *below* zero they survive once on their doggy life — the next time, they're out.
- A non-killer hitting someone else's number has no effect (you have to earn the right to
  hunt first).

No build step, no dependencies — it's one `index.html` file.

## Run it locally

Just open `index.html` in a browser, or serve it:

```bash
cd killer-darts-scorer
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Host it on GitHub Pages

This repo is already pushed to `github.com/mharry97/killer-darts-scorer`. To turn on Pages:

1. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
   branch `main`, folder `/ (root)`. Save.
2. Your scorer will be live at `https://mharry97.github.io/killer-darts-scorer/`
   after a minute or two.

## Notes

- Game state (players, throw log) is saved to the browser's `localStorage`, so refreshing
  the page mid-game won't lose progress. It's per-device/browser, not shared between phones
  — one person scores on their phone for the whole group.
- Tap a player's card to make them the current thrower (handy if turn order needs a manual
  nudge). Turns auto-advance after 3 darts, or tap "End turn" early.
- "Undo last dart" reverses the most recently logged throw.
