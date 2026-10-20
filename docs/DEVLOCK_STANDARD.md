# Dev Lock Standard

## Required devlog fields

Every session submission must contain:

- student name and GitHub username
- session number and title
- submission date
- short summary of what was learned
- answers or notes for the session topics
- work performed, with commands or step-by-step actions
- evidence links
- blockers and next step

## Evidence quality

Evidence should be direct and reviewable:

- GitHub commit or repository URL
- repository or file URL
- blockchain explorer URL and transaction hash
- screenshot with visible context
- terminal output copied into a fenced code block

Use at least one primary evidence link for every practical task. A link to a
homepage without the relevant file, transaction, or result is not sufficient.

## Practical-session safety

Use testnet wallets and faucet tokens only. Never submit seed phrases, private
keys, raw wallet backups, or secrets. Redact them before sharing screenshots.

## Review checklist

- The devlog is in `submissions/<github-username>/session-XX.md`.
- The session number and title match the schedule.
- Evidence links open and point to the claimed result.
- The commit history shows the work was submitted before the deadline.
- No secret or personal credential is present.
- The submitted repository URL points to the student's own GitHub repository.
