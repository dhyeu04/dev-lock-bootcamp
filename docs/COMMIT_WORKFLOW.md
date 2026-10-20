# Commit Workflow Example

Run these commands after creating an empty GitHub repository for yourself:

```bash
git clone https://github.com/vantuann205/dev-lock-bootcamp.git
cd dev-lock-bootcamp
git remote set-url origin https://github.com/<github-username>/<your-repo>.git
Copy-Item templates/session-devlog.md submissions/<github-username>/session-01.md
# edit the copied file and add evidence
git status
git add submissions/<github-username>/session-01.md
git commit -m "[S01] add devlog - @github-username"
git push -u origin main
```

Repeat the same flow for each session. Send your own repository URL to the
instructor for review. Keep unrelated files out of the commit.

## What reviewers look at

1. The commit changes the correct session file.
2. The message identifies the session and author.
3. The devlog contains evidence that can be opened and checked.
4. The commit was pushed before the deadline.
