# keystroke

A minimalist, browser-based typing speed test — no installs, no accounts, no distractions. Open the HTML file and start typing.

---

## Features

**Test modes**
- **Time** — type as many words as you can in 15, 30, or 60 seconds
- **Words** — complete a set number of words (10, 25, or 50)

**Modifiers**
- **Punctuation** — adds commas, periods, and question marks to the word set
- **Numbers** — randomly inserts two-digit numbers into the flow
- **No Mistake (Sudden Death)** — any error instantly ends the test

**Live HUD** — real-time WPM and accuracy visible while you type

**Results dashboard** — net WPM, raw WPM, accuracy, character breakdown, consistency score, and a performance timeline chart

**Audio feedback** — subtle click sounds on correct keystrokes, a lower tone on errors (Web Audio API, no external files)

**Themes** — four built-in visual themes:

| Name | Style |
|------|-------|
| `zinc` | Dark, neutral zinc tones |
| `glass` | Light frosted glass |
| `nord` | Cool blue-grey nord palette |
| `sepia` | Warm paper-like tones |

---

## Usage

No build step. Just open `keystroke_v3_1.html` in any modern browser.

```
open keystroke_v3_1.html
```

**Controls**

| Key | Action |
|-----|--------|
| Any letter key | Start test / type |
| `Space` | Advance to next word |
| `Backspace` | Delete last character |
| `Tab` or `Esc` | Restart test instantly |
| `Enter` | Restart after results screen |

---

## How it works

The word set is drawn from the top 100 most common English words (max 8 characters). Words are randomly sampled each session so no two tests are identical.

**WPM calculation** follows the standard definition: every 5 correct characters = 1 word.

- **Net WPM** — correct characters only, divided by time
- **Raw WPM** — all keystrokes, divided by time
- **Consistency** — measures how stable your WPM was across the test (lower variance = higher score)

The caret tracks character position in real time using `requestAnimationFrame` and CSS `translate3d` for smooth, lag-free movement. It blinks while idle and goes solid the moment you start typing.

---

## File structure

Everything is self-contained in a single HTML file — no dependencies, no CDN calls, no external fonts loaded at runtime beyond Google Fonts.

```
keystroke_v3_1.html   ← the entire app
README.md
```

---

## Browser support

Works in any browser with ES2020 support and Web Audio API — Chrome, Firefox, Safari, Edge. No polyfills needed.

---

## Customisation

All theme variables are CSS custom properties on `:root[data-theme="..."]` at the top of the `<style>` block — easy to add a new theme by copying any existing block and changing the colour values.

The word bank is a plain array near the top of the `<script>` block. Swap it out for any word list you like.
