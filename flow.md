# Development Flow

## Git & GitHub workflow

After every meaningful piece of work, commit the changes and push to GitHub immediately. This ensures we always have a recoverable saved state and can revert to any previous version if something goes wrong.

### Rules

- **Commit after every change** — don't batch multiple unrelated changes into one commit.
- **Push immediately after committing** — never leave commits sitting only on the local machine.
- **Write clean, descriptive commit messages** — subject line summarizes what changed and why (e.g. `Add speed cap to pipe acceleration` not `update game`).
- **Never force-push** to `master` — always add new commits instead of rewriting history.

### Commit message format

```
Short subject line (50 chars or less)

Optional body explaining the why if the subject isn't enough.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>
```

### Quick reference

```powershell
# Stage specific files
git add <file1> <file2>

# Commit (PowerShell here-string — required on this machine)
git commit -m @'
Subject line here

Body if needed.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>
'@

# Push
git push
```

### Repository

Remote: https://github.com/ugnaysolutions/jumpy-cat  
Branch: `master`
