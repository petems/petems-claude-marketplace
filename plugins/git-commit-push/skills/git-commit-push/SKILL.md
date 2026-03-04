---
name: git-commit-push
description: "Stage all changes, write a Conventional Commits message, commit, and push to remote in one go. Use this skill whenever the user says 'commit', 'push', 'commit and push', 'git push', 'ship it', 'save and push', 'send it', 'push my changes', or any variation that implies they want their current work committed and pushed to the remote. Trigger even if the user is casual or brief — if the intent is to get changes into the remote repo, this skill applies."
---

# Git Commit & Push

Stage all changes, craft a Conventional Commits message with a bullet-point body, commit, and push — all in one flow.

## Why this exists

Committing and pushing is one of the most common developer actions, but writing good commit messages takes thought. This skill removes the friction: it analyzes the actual diff, writes a meaningful message, and gets the code to the remote in one step. The user should see exactly what happened at each stage so nothing feels like a black box.

## Workflow

### 1. Check the current state

Run `git status` and `git diff --stat` to understand what changed. If there are no changes (working tree clean, nothing staged), tell the user there's nothing to commit and stop.

### 2. Stage all changes

Run `git add -A` to stage everything — tracked, untracked, and deleted files.

**Exception**: If you spot files that look like secrets or sensitive data (`.env`, `credentials.json`, private keys, files with `secret` or `token` in the name), warn the user before staging and ask if they want to proceed. Don't silently commit secrets.

### 3. Analyze the diff

Run `git diff --cached` to see exactly what's staged. Read the diff carefully — the commit message quality depends on understanding what actually changed, not just which files were touched.

Look for:
* What feature, fix, or change does this represent?
* Are there multiple logical changes that would normally be separate commits? If so, mention this to the user but proceed with a single commit unless they say otherwise.
* What's the most accurate Conventional Commits type?

### 4. Write the commit message

Use Conventional Commits format with a bullet-point body:

```
<type>(<optional scope>): <short summary>

* First change or detail
* Second change or detail
* Third change or detail
```

**Type selection guide:**
* `feat` — new functionality for the user
* `fix` — bug fix
* `docs` — documentation only
* `style` — formatting, whitespace, semicolons (no logic change)
* `refactor` — code restructuring without behavior change
* `test` — adding or updating tests
* `chore` — build, CI, dependencies, tooling
* `perf` — performance improvement

**Message rules:**
* Summary line: imperative mood, lowercase, no period, under 72 characters
* Body bullets use `*` (not `-`)
* Each bullet should describe a specific change, not repeat the summary
* Be concrete — mention file names, function names, or config keys when it helps clarity
* If there's a breaking change, add `BREAKING CHANGE:` in the footer

**Example:**

```
feat(auth): add JWT token refresh on expiry

* Add refresh token rotation in AuthProvider
* Update middleware to check token expiry before API calls
* Add TOKEN_REFRESH_INTERVAL to config defaults
```

### 5. Commit

Run the commit with the crafted message. Use a heredoc to preserve formatting:

```bash
git commit -m "$(cat <<'EOF'
<the commit message>
EOF
)"
```

### 6. Push

Push to the remote. If the current branch doesn't track a remote branch yet, set the upstream automatically:

```bash
git push -u origin HEAD
```

If the branch already tracks a remote, a regular `git push` is fine.

### 7. Show the results

Display to the user:
1. The full commit message that was used
2. The output from `git commit` (files changed, insertions, deletions)
3. The output from `git push` (remote URL, branch, any new branch info)

Format it clearly so the user can see exactly what happened.

## Edge cases

* **Empty diff after staging**: This can happen if all changes were already staged. Check `git diff --cached` — if it's empty too, tell the user there's nothing new to commit.
* **Push rejected**: If the push fails (e.g., remote has new commits), tell the user. Don't force-push. Suggest they pull and resolve first.
* **Detached HEAD**: Warn the user they're not on a branch and ask what they want to do before committing.
* **Merge conflicts in staging**: If `git add -A` picks up conflict markers, warn the user that unresolved conflicts exist.
