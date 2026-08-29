# Loopbank — Adaptive Problem Trainer

Open `index.html` in a modern browser. No install is required.

## Current interface

Loopbank uses a clean white, practice-test-style interface. The bank library is its own home page; there is no bank sidebar. Clicking a bank opens a dedicated bank page with its questions, progress, export/delete controls, and a **Back to banks** button.

Generation 0 banks can be renamed from either:

- the pencil button on the Generation 0 card in the bank library, or
- the **Rename** control at the top of the Generation 0 bank page.

Later generations inherit that name automatically and do not have separate rename controls. The generation label is displayed inline beside the bank name, using its own compact monospace styling.

On the solving page, the question identifier is shown compactly as **Question X** rather than as a separate oversized question number.

## CSV format

```csv
question_number,source_url
1,https://example.com/question/1
2,https://example.com/question/2
```

The header is optional. The app uses the first two columns.

## Accounts and automatic saving

Loopbank uses a username and password. Each browser-local account keeps its own question banks, generations, names, answers, and checkpoints.

This is a standalone static website, so accounts are local to the browser rather than server-backed. A salted password verifier is stored locally; the plaintext password is not stored. Cross-device sync would require a backend/database.

## Live adaptive generations

- As soon as you begin using Generation X, Loopbank creates Generation X+1 as a live-building bank.
- Every question marked **Need to review** is added to the next generation immediately.
- As review need grows, reinforcement questions from the original bank are added too.
- The next bank appears in the bank library while it is building and unlocks when the current generation is complete.
- If a generation finishes with zero review-needed questions, the empty next-generation placeholder is removed.

## Bank management

- Each bank is its own page/view rather than being selected from a sidebar.
- Only Generation 0 banks are directly renamable; later generations inherit the Generation 0 name.
- Every bank has its own delete option.
- Deleting a generation also deletes later generations that depend on it.
- The active bank can be exported to CSV or reset with **Redo this bank**.

## Undo

- **Undo last** works while solving and after the final answer.
- Undo restores the previous question to unanswered and recalculates the live next-generation queue.
- Undo is disabled for an earlier generation after a later generation has already been started, protecting dependent progress.

## Shortcuts

- `1` — Correct & confident
- `2` — Need to review
- `U` — Undo the most recent classification
- `Ctrl+Z` / `Cmd+Z` — Undo the most recent classification


## Styling

The visual design lives in `styles.css`. It uses Fraunces for display headings, Manrope for interface text, and IBM Plex Mono for status/progress details, with system fallbacks. The interface remains primarily white with Bluebook-inspired structure and subtle blue accents.


## Generation naming

- Imported CSV banks are **Generation 0**.
- The first adaptive review copy is **Generation 1**, followed by Generation 2, and so on.
- Only Generation 0 can be renamed. Its later generations automatically inherit the same bank name.
