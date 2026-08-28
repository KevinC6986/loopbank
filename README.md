# Loopbank — Adaptive Problem Trainer

Open `index.html` in a modern browser. No server or install is required.

## CSV format

```csv
question_number,source_url
1,https://example.com/question/1
2,https://example.com/question/2
```

The header row is optional. The app uses only the first two columns.

## How adaptive review works

1. Every answer is autosaved in `localStorage` immediately.
2. When a bank is completed, every question marked **Need to review** is carried into the next generation.
3. The next bank also adds reinforcement questions from the original imported bank. The number added rises with the miss rate, and the selected questions are the nearest question numbers to the missed ones, while preferring questions that were not just seen in the parent bank.
4. Finishing that review bank repeats the same process, creating Generation 3, Generation 4, and so on.
5. If a generation has zero review marks, that branch is complete and no new bank is generated.

The app also lets you export the active generation as CSV, redo a generation, and resume from the last unfinished checkpoint after closing/reopening the page.

## Local profiles / sign in

The **Sign in** control creates a browser-local profile using a name and email. Each profile gets its own saved banks and checkpoints on that browser. Because this project is a standalone static site, this is not server-backed authentication: no password is stored or transmitted, and the profile does not sync across devices. Existing data from the original version is preserved as guest data; when a new profile is first created, current guest banks are copied into it.

## Collapsible bank sidebar

Use the arrow button at the top of the Question Bank panel to collapse or expand the sidebar. The preference is remembered in the browser.
