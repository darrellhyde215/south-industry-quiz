# Southern Road Trip

A single-file browser study game for **US Geography: The South — Part II: Southern Cities & Industries**.

Open `index.html` in any browser. No install, no network, no build step.

- **Play** — 19 questions drawn from the worksheet: multiple choice, true/false,
  pick-every-right-answer, and one type-in. Points, streak bonus, and a second
  pass over whatever was missed.
- **Study guide** — every fact on one scrollable page.
- Keyboard: `1`–`9` to pick, `Enter` to check / advance. Light + dark theme.

Answers follow the official answer key (© C. Page). Worksheet content is
third-party copyright — this repo is private, for personal study use only.

## Adding questions later

Everything lives in `index.html`. Two data structures near the bottom, both plain arrays:

- `BANK` — the questions. `n` is the worksheet number it came from, and `type` is one of:
  - `mc` — `opts: [...]`, `a: <index of the right one>`
  - `tf` — `a: true | false`
  - `multi` — `opts: [...]`, `a: [indexes of every right one]` (all must be picked)
  - `type` — `accept: ["answer"]`, optional `hint`; matching ignores case and punctuation
  - every item needs a `why`, shown after answering
- `STUDY` — the study-guide view: sections of `[term, definition]`, with an optional third
  element `[...]` that renders as hot-spot chips.

Option order is shuffled at runtime, so write `a` against the order in `opts`.

## Testing

`test/drive.html` plays the whole game in a headless browser and checks every grade.
The command is in a comment at the top of that file. Any `FAIL` line in the output is real.
