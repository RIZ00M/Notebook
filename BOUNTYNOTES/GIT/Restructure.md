# Resetting / Restructuring a Git Project

Commands to wipe the git history of a project and push a clean `main` branch.

```bash
cd /path/to/your/project

git init
git remote -v
git add -A
git commit -m "Reset project structure"

git branch -M main
git push -u origin main --force
```

| Command | Purpose |
|---|---|
| `cd /path/to/your/project` | Move into the project directory |
| `git init` | (Re)initialise the git repository |
| `git remote -v` | Verify the remote(s) currently configured |
| `git add -A` | Stage all files (new, modified, deleted) |
| `git commit -m "Reset project structure"` | Commit the staged changes |
| `git branch -M main` | Rename the current branch to `main` |
| `git push -u origin main --force` | Force-push `main` to the remote, overwriting its history |

⚠️ **Note:** `--force` overwrites the remote history — use with care on shared repos.
