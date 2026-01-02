# Rebase

It moves your commits on top of another branch's latest commit.

![merge vs rebase](./git%20merge%20vs%20git%20rebase.png)

## Why rebase?

- Keeps commit history clean & linear
- Avoids unnecessary merge commits
- Makes logs easier to read (git log)

> Always run `git rebase <target-branch>` while you are on the branch you want to move (shift).

> Rebase happens if the current branch has commits that the target branch does not.

## When rebase happens?

### Feature is ahead of main (most common)

```
main:     A --- B --- C
feature:  A --- B --- C --- D --- E
```

`git checkout feature`

`git rebase main`

**What Git does:**

- Takes commits D, E
- Replays them on top of C
- Creates new commits D', E'

```
main:     A --- B --- C
feature:                  D' --- E'
```

### Feature and main diverged (still rebases)

```
main:     A --- B --- C --- F
feature:  A --- B --- C --- D --- E
```

`git checkout feature`

`git rebase main`

**What happens:**

- Git finds D, E (unique to feature)
- Replays them on top of F

```
main:     A --- B --- C --- F
feature:                      D' --- E'
```

## rebase conflict

- Resolve all conflicts manually, mark them as resolved with
- "git add/rm <conflicted_files>", then run "git rebase --continue".
- You can instead skip this commit: run "git rebase --skip".
- To abort and get back to the state before "git rebase", run "git rebase --abort".
