# 🎴 ONO 99

A fully playable browser-based implementation of the **ONO 99** card game, built as a single self-contained HTML file. No installation, no server, no dependencies — just open and play.

---

## 🎮 How to Play

Open `ono99_v7.html` in any modern browser. That's it.

- Enter your name on the title screen
- Choose 1, 2, or 3 computer opponents
- Hit **▶ Play!**

**Goal:** Be the last player still in the game. Play cards onto the discard pile and keep the running total *under* 99. If you can't play any card without hitting 99 or above — you're out.

---

## 🃏 Card Reference

| Card | Effect |
|---|---|
| **2–9** | Add face value to the total |
| **10** | Add 10 to the total |
| **−10** | Subtract 10 (total can't go below 0) |
| **Hold** | Total unchanged — pass to next player |
| **Reverse** | Total unchanged — reverses direction of play (acts as Hold with 2 players) |
| **Play 2** | Next player must take two full turns. They can deflect with a Reverse (bounces back) or another Play 2 (passes it forward) |
| **ONO 99** | Cannot be played. Deadweight in your hand. If you collect all 4, discard your entire hand and draw 4 new cards |

---

## ✨ Features

- **Full 2022 rules** — 112-card deck, Play 2, ONO 99 escape rule
- **Voice announcements** — the game speaks every equation out loud: *"47 plus 8 equals 55"*, *"Oh no, 99!"*, *"Jake wins! Amazing!"*
- **Visual equations** — every card play shows the full arithmetic (e.g. `76 + 4 = 80`) above the running total
- **Background music & sound effects** — extracted from a Scratch UNO project (sb3)
- **Smart AI opponents** — Rex, Zara, and Blitz play strategically: save helper cards for danger, burn high numbers early
- **Table layout** — opponents positioned left, top, and right around the center piles, just like the physical game
- **Personalized** — enter your name; the game addresses you by name throughout, including the win/loss announcement
- **Color-coded danger** — total display shifts from cyan → orange → red as you approach 99
- **Self-contained** — all assets (music, sounds, background image) are base64-encoded inside the HTML file

---

## 🎵 Audio Assets

Sound effects and music are sourced from a Scratch UNO Flip remix project (sb3 format). The following assets are embedded:

| Asset | Source name in sb3 |
|---|---|
| Background music | `music: song 2` |
| Card shuffle | `sfx: shuffle pack` |
| Card play | `sfx: bloop` |
| Special card | `sfx: draw fast` |
| Game start | `sfx: game start beep` |
| Winner fanfare | `music: winner` |

Voice announcements (equations, "Oh no 99!", player names) use the browser's built-in **Web Speech API** — no external TTS service required.

---

## 📐 Deck Composition (112 cards)

| Card | Count |
|---|---|
| Numbers 2–9 | 6 of each = 48 |
| 10 | 18 |
| Hold | 8 |
| Reverse | 12 |
| −10 | 8 |
| Play 2 | 8 |
| ONO 99 | 10 |
| **Total** | **112** |

---

## 🤖 AI Strategy

The computer opponents (Rex, Zara, Blitz) use a three-tier decision system:

- **Total < 60:** Play high number cards aggressively; save helper cards
- **Total 60–85:** Play the highest safe number card available
- **Total > 85:** Prioritize −10 → Hold → Play 2 → Reverse before touching number cards

When hit by a Play 2, the AI will deflect with a Reverse if the total is already high.

---

## 🛠 Technical Notes

- Pure HTML/CSS/JavaScript — no frameworks, no build step
- Web Speech API for TTS (works in Chrome, Safari, Edge, Firefox)
- Speech is fully queued — each announcement waits for the previous one to finish before the next turn begins
- Audio context is initialized on first user interaction to comply with browser autoplay policies
- All assets base64-encoded; file size is approximately 4MB

---

## 🚀 Hosting

Since it's a single file, you can host it anywhere:

```
# GitHub Pages: just drop ono99.html in your repo root
# Or serve locally:
python3 -m http.server 8000
# then open http://localhost:8000/ono99.html
```

---

## 📄 License

This is a fan-made implementation for personal use.  
Audio assets sourced from a Scratch community project.
