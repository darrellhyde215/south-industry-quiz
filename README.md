# Southern Road Trip

A single-file browser study game for **US Geography: The South**, covering
Part I (The Land of the South) and Part II (Southern Cities & Industries).

Open `index.html` in any browser. No install, no network, no build step.

- **Pick your content** — study one worksheet or all of them. The choice is remembered
  on the device, and a URL hash preselects a worksheet (`index.html#part1`).
- **Play** — 43 questions drawn from the worksheets: multiple choice, true/false,
  pick-every-right-answer, and type-ins. Points, streak bonus, a second pass over
  whatever was missed, and a per-worksheet score breakdown when more than one is picked.
- **Study guide** — every fact on one scrollable page.
- Keyboard: `1`–`9` to pick, `Enter` to check / advance. Light + dark theme.

Answers follow the official answer key (© C. Page). Worksheet content is
third-party copyright — this repo is private, for personal study use only.

## Adding questions later

Everything lives in `index.html`, in the `DECKS` array near the bottom. One entry per
worksheet: `id` (also the URL hash), `chip` (picker label), `title`, `bank`, `study`.
Adding another document means appending another deck — no logic changes.

- `bank` — the questions. `n` is the worksheet number it came from, and `type` is one of:
  - `mc` — `opts: [...]`, `a: <index of the right one>`
  - `tf` — `a: true | false`
  - `multi` — `opts: [...]`, `a: [indexes of every right one]` (all must be picked)
  - `type` — `accept: ["answer"]`, optional `hint`; matching ignores case and punctuation
  - every item needs a `why`, shown after answering
- `study` — the study-guide view: sections of `[term, definition]`, with an optional third
  element `[...]` that renders as chips.

Option order is shuffled at runtime, so write `a` against the order in `opts`.

## Testing

`test/drive.html` plays the whole game in a headless browser and checks every grade.
The command is in a comment at the top of that file. Any `FAIL` line in the output is real.
