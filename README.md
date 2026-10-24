# THE TERMINAL DREAMS

> THE MACHINE IS SILENT. PRESS ANY KEY TO WAKE IT.

A web oracle whose every glyph is dreamed, live, by a 2017 neural
network. You type in letters; it answers in digits — the only alphabet
it was ever taught.

**Play:** https://YOURNAME.github.io/terminal-dreams/

Desktop browser recommended. Headphones recommended. No account, no
server, nothing leaves your machine.

┌────────────────────────────────────────────────────┐ │ ▟▙ ▗▟▟ ▙▗ ▟▟▗ ▗▟▟ ▙▗▙ ▟▗ ▟▙▗ ▗▟▙ │ │ │ │ (every character above is a 28×28 digit, │ │ dreamed live by the model in this folder) │ │ │ │ > WILL I PASS_ │ │ │ │ YES. IN SOME ORDER OF DIGITS. │ │ READING #1 · SEED a3f91c │ │ the same words will always dream the same dream │ └────────────────────────────────────────────────────┘


## Concept

*The Terminal Dreams* is a piece about constraint as a creative force.
Its entire engine is one of the earliest usable generative models — a
2017 ACGAN trained on MNIST, a network that knows exactly ten symbols
at 28×28 pixels and nothing else. Instead of correcting that poverty,
the work is built entirely out of it: your words cannot be read, only
re-dreamed as digits; its answers are limited to its ten-symbol
vocabulary; its uncertainty (states between symbols it was never
taught) is displayed, not hidden.

The machine is also *honest in the only way it can be*: every reading is
seeded from your words alone, so the same question always dreams the
same dream — today, tomorrow, after a refresh, forever. A receipt can
be exported of any reading, marked with the promise that it is
perfectly repeatable — if you ask again in the same words.

## The Law Book

The piece was built by writing these laws first and refusing to break
them. Every amendment is visible in the footer of the page.

1. Every glyph is dreamed live by a 2017 neural network (the model file in this folder).
2. The machine hears no language. Your words are only seeds.
3. Its output is 28×28 pixels. It is shown at 28×28, magnified as a loupe, nothing invented.
4. Nothing is corrected.
5. The same words always dream the same dream.
6. The in-between is also dreamed. Uncertainty is shown, not hidden.
7. The noise that shaped each dream is played, not hidden.
8. The ledger is kept. Nothing is forgotten.

## Controls

| Input | Action |
|---|---|
| type, then **Enter** | a reading — your words are dreamed back, then answered |
| **[G]** | the vocabulary: all 80 dreams, visibly re-dreaming (watched, it dreams faster) |
| **[I]** | the in-between: walk between two symbols through states it was never taught |
| **← →** | walk the in-between (in that mode) |
| **↑ ↓** | change the symbols being interpolated |
| **[R]** | export the last reading as a PNG receipt |
| **[M]** | mute / unmute everything |
| **[ESC]** | return to speaking |

All bracket commands are also clickable buttons. Sound is entirely
synthesized: the ten symbols have ten pentatonic notes, every re-dream
of the alphabet chimes softly, and each reading plays the actual
100-dimensional noise vector that shaped it as a glassy chord.

## How it works

- **The model** is an ACGAN generator (Odena, Olah & Shlens, 2017 —
  *Conditional Image Synthesis with Auxiliary Classifier GANs*) trained
  on MNIST, ~1 MB, committed to this repository like a sprite sheet and
  running entirely in your browser through TensorFlow.js. It takes a
  100-dimensional noise vector and a class index, and dreams a digit.
- **Determinism:** your question is normalized and hashed (FNV-1a);
  the hash seeds the noise for every glyph of the reading. No
  timestamps, no session values enter the seed — so determinism is
  relative only to the model file. Retrain the oracle and it will
  change its mind.
- **Living vs. eternal text:** ambient text renders from a pool that
  re-dreams itself every 650 ms; oracle readings are dreamed exactly
  once from the question's seed and frozen forever.
- **The in-between** feeds the generator fractional class values
  (e.g. 5.47) that never appeared in its training — the middle of each
  strip is genuine out-of-distribution uncertainty, shown raw.
- **The ledger** stores your readings (words, seed, timestamp) in your
  browser's localStorage — capped at 200, never transmitted anywhere.
  Returning visitors are greeted with their own last words, re-dreamed
  identically.

Retrain your own oracle
The generator comes from the official TensorFlow.js example (tensorflow/tfjs-examples — mnist-acgan, Apache 2.0):


## Credits & licenses
- Generator model: TensorFlow.js mnist-acgan example — Apache 2.0, Google LLC. (If you trained the weights yourself, credit it as: "Generator trained by the artist using the TensorFlow.js mnist-acgan example (Apache 2.0), Google LLC.")

- Runtime: TensorFlow.js (Apache 2.0)

- Typeface: VT323 by Peter Hull (Google Fonts, SIL OFL)

- Design, laws, oracle, soundscape, receipts, ledger: the artist.
- This piece: CC BY-NC 4.0 — play, study, exhibit; do not resell.
- Influences:
 Sol LeWitt ("the idea becomes a machine that makes the art") · Harold Cohen's AARON (1973–2016) · Mordvintsev, Olah & Tyka, Inceptionism (2015) · the long tradition of seeded divination, from the I Ching onward — in this piece, your words are literally only seeds.
