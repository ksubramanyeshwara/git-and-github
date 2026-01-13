# Working with Remote

- Local repo: where you work.
- Remote repo: shared copy (GitHub/GitLab)

## Git fetch

- Downloads the new data (new commits, branches, and tags) from remote repo.
- Updates remote-tracking branches.
- It does not merge(rebase) it into your local repo automatically.

```
GitHub main
     ↓
remotes/origin/main   ← updated by fetch
     ↓
main                  ← updated by merge/rebase
```

## Git pull

- It fetches changes.
- Immediately merges into your current branch.

- If you do `git pull origin main`
- Internally `git fetch origin` `git merge origin/main`

## Git pull vs pull --rebase

**Scenario: You + Teammate**

- You clone repo
- Teammate pushes new commit to main
- You also make commits locally
- Now history looks like this:

```
A --- B --- C   (origin/main)
       \
        D --- E   (your local main)
```

Git now must decide: merge? rebase?

> In git pull default is merge. If you want rebase you have to explicitly specify it.

**git pull**

```
A --- B --- C ---- M
       \         /
        D --- E -
```

- Creates a merge commit
- History becomes non-linear
- Safe, but noisy

**git pull --rebase**

```
A --- B --- C --- D' --- E'
```

- Linear history
- Cleaner PRs
- Rewrites commit hashes

### When to use which?

- Use plain `git pull` (merge) when you want to preserve the true history of parallel work.
- Use `git pull --rebase` when you prefer a clean, linear history (common in feature branches).

## Upstream Branch

- It is an remote branch that local branch tracks.
- It links your local/remote branches.

**Set upstream branch**

- `git push -u origin feature-login`

**View upstream**

`git branch -vv` Check tracking branches

## Divergence Scenarios

- You make commits locally.
- Someone else pushes commits to the same branch on the remote.
- Now your local branch and origin/branch have diverged.

```
Remote:   A -- B -- C -- E
                 \
Local:            C -- D
```

> Always `git fetch` first to see what's new. Based on new data decide: merge or rebase?

> Divergence is normal in collaborative work. Prefer rebase for feature branches (clean history) and merge for long-lived branches like main (preserve true history).
