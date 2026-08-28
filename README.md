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
