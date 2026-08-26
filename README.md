# Killer Darts Scorer

A single-page, phone-first scorer for the darts game **Killer**. You just tap what was
thrown (single/double/triple + number) and the app derives lives and killer status from
the log — no manual score-fiddling.

## Rules it implements

- Each player claims a number (1–20). Everyone starts on **0 lives** — there's no preset pool.
- Hitting your own number builds your lives up: single = +1, double = +2, triple = +3.
  Reach **3** and you become a killer.
- Once a player is a killer, an opponent hitting their number brings their lives back down
  the same way (single −1, double −2, triple −3).
- By default, a killer hitting their **own** number does nothing further. Turning on
  **hard mode** makes those self-hits cost lives too, same as being hit by someone else.
- Optional **doggy life** rule: reaching 0 lives is safe, but the first hit that would take
  a player *below* zero is survived once — the next time it happens, they're out.
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

## Notes

- Game state (players, throw log) is saved to the browser's `localStorage`, so refreshing
  the page mid-game won't lose progress. It's per-device/browser, not shared between phones
  — one person scores on their phone for the whole group.
- Tap a player's card to make them the current thrower (handy if turn order needs a manual
  nudge). Turns auto-advance after 3 darts, or tap "End turn" early.
- "Undo last dart" reverses the most recently logged throw.
