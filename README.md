# Loopbank — Adaptive Problem Trainer

Open `index.html` in a modern browser. No install is required.

## CSV format

```csv
question_number,source_url
1,https://example.com/question/1
2,https://example.com/question/2
```

The header is optional. The app uses the first two columns.

## Accounts and automatic saving

Loopbank now requires a **username and password**. You can create an account from the sign-in screen and then sign in later with the same credentials.

This is still a standalone static website, so accounts are **local to the browser** rather than server-backed. A salted password verifier is stored locally; the plaintext password is not stored. Every account gets its own question-bank data and checkpoints in browser storage, and all changes save automatically.

For true cloud accounts, cross-device sync, password recovery, and stronger authentication, the next step would be connecting this UI to a backend/database.

## Live adaptive generations

- As soon as you begin using Generation X, Loopbank creates Generation X+1 as a **Building live** bank.
- Every question marked **Need to review** is added to the next generation immediately.
- As the number/rate of review-needed questions rises, the next generation also gains reinforcement questions from the original source bank.
- Reinforcement is selected from nearby question numbers and prefers questions that were not just used in the current generation.
- The live bank remains visible in the sidebar while you work and unlocks when Generation X is complete.
- If Generation X finishes with zero review-needed questions, its empty next-generation placeholder is removed and the branch ends.

## Bank management

- The left bank sidebar is collapsible, and that preference is remembered.
- Every bank has its own **× delete** button.
- Deleting a generation also deletes later generations that depend on it.
- There is no global “remove local data” control.
- You can export the active generation to CSV or redo a generation.

## Shortcuts

- `1` — Correct & confident
- `2` — Need to review
