# How to use Git and GitHub

A one-page workflow for contributing to this cookbook. It uses the **fork +
pull request** model that Project Pythia repositories follow. The golden rule:

> **Treat your fork's `main` as a read-only mirror of upstream. Never commit to
> it. Branch for every change.**

Follow that and your fork stays clean and your pull requests stay easy to review.

## One-time setup

1. **Fork** the repository on GitHub (the "Fork" button), then clone *your*
   fork:

   ```bash
   git clone git@github.com:<your-username>/geomorphology-cookbook.git
   cd geomorphology-cookbook
   ```

2. Add the canonical repository as a second remote named `upstream`. `origin`
   stays pointed at your fork; `upstream` points at the shared project:

   ```bash
   git remote add upstream git@github.com:ProjectPythia/geomorphology-cookbook.git
   git remote -v   # confirm: origin = your fork, upstream = ProjectPythia
   ```

3. Tell Git to refuse "merge bubbles" on pull. This makes `git pull`
   fast-forward or stop with an error instead of silently creating an extra
   merge commit:

   ```bash
   git config pull.ff only
   ```

## The everyday loop

### 1. Sync `main`, then branch

Always start from an up-to-date `main`, and do your work on a feature branch:

```bash
git checkout main
git fetch upstream
git merge --ff-only upstream/main   # fast-forwards; errors if main has stray commits
git push origin main                # keep your fork's main current too

git checkout -b my-feature          # name it for the change you're making
```

### 2. Work and commit

```bash
git add <files>
git commit -m "Short, clear description of the change"
```

Commit in logical chunks with messages that explain *why*, not just *what*.

### 3. Push and open a pull request

```bash
git push -u origin my-feature
```

Then open a PR on GitHub from `my-feature` into `ProjectPythia:main`. Use the
GitHub UI, or the [`gh` CLI](https://cli.github.com/):

```bash
gh pr create --repo ProjectPythia/geomorphology-cookbook --fill
```

### 4. Respond to review

Push more commits to the same branch; they appear on the PR automatically:

```bash
git add <files> && git commit -m "Address review feedback"
git push
```

### 5. After it merges, clean up

```bash
git checkout main
git fetch upstream
git merge --ff-only upstream/main   # your work is now here, via the merge
git push origin main

git branch -d my-feature                 # delete the local branch
git push origin --delete my-feature      # delete it on your fork
```

## Keeping a long-running branch current

If `upstream/main` moves while you're still working, rebase your branch on top
of it so your PR stays conflict-free and replays cleanly:

```bash
git fetch upstream
git checkout my-feature
git rebase upstream/main
# resolve any conflicts, then:
git push --force-with-lease
```

Use `--force-with-lease` (not `--force`) — it refuses to overwrite work you
haven't seen yet.

## Troubleshooting

| Symptom | Cause | Fix |
| --- | --- | --- |
| `git merge --ff-only` fails with *"Not possible to fast-forward"* | You committed directly to `main`. | Move the work: `git branch my-feature`, then `git reset --hard upstream/main`. |
| Your fork's `main` shows *"N commits ahead"* on GitHub | Merge commits landed on `main` (e.g. the "Sync fork" button used a merge). | Reset to upstream: `git checkout main && git fetch upstream && git reset --hard upstream/main && git push --force-with-lease origin main`. |
| GitHub's **Sync fork** offers *"Discard N commits"* | Same as above — `main` diverged. | Discard them; `main` should mirror upstream exactly. |

## Why this matters

When your PR is merged, the project often **squashes** it into a single new
commit with a different ID than your local commits. If you also had that work on
your `main`, the two histories can no longer fast-forward — they can only
*merge*, producing a "bubble" (an extra merge commit) and an "N commits ahead"
fork. Keeping `main` a pristine mirror and branching for every change avoids this
entirely.
