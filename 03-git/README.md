# 03 - Git (Deep)

## Why Deep Git
You use Git every day but probably only use 10% of it. The other 90% saves you when things go wrong — and things always go wrong.

## What to Learn (Week 1)

### Internals
- [ ] Git object model — blobs, trees, commits, tags
- [ ] How refs work — branches are just pointers to commits
- [ ] The reflog — your safety net for "I just lost my work"
- [ ] How merges actually work — three-way merge, merge bases

### Advanced Operations
- [ ] Interactive rebase — squashing, reordering, editing commits (`git rebase -i`)
- [ ] Cherry-pick — when and how
- [ ] `git bisect` — binary search for the commit that broke something
- [ ] `git stash` — including `stash pop`, `stash apply`, `stash list`, `stash show -p`
- [ ] `git worktree` — work on multiple branches simultaneously
- [ ] `git blame` and `git log -S` (pickaxe search)
- [ ] `git diff` — staged vs unstaged, between branches, between commits

### Branching Strategies
- [ ] Trunk-based development (preferred for CI/CD)
- [ ] Git Flow (know it, but understand why trunk-based is often better)
- [ ] Feature flags as alternative to long-lived branches

### Hooks & Automation
- [ ] Pre-commit hooks — linting, formatting, secret scanning
- [ ] Pre-push hooks
- [ ] Server-side hooks (in GitHub context: branch protection, required checks)
- [ ] Tools: `pre-commit` framework, `husky`

### GitHub Specifics
- [ ] Branch protection rules and rulesets
- [ ] CODEOWNERS
- [ ] GitHub Actions integration with branch rules
- [ ] Signed commits (GPG/SSH signing)
- [ ] GitHub CLI (`gh`) for automation

## Hands-On Project

**Create a Git workflow automation toolkit:**
1. Set up a repo with branch protection, required reviews, required CI checks
2. Write pre-commit hooks that: lint code, check for secrets, validate commit message format
3. Use `git bisect` to find a deliberately introduced bug in a repo with 50+ commits
4. Practice disaster recovery: simulate losing commits, force-push recovery, detached HEAD fixes
5. Write a script that generates a changelog from conventional commits

## Validation
You're done when you can:
- Recover from any git disaster without Googling
- Rewrite history cleanly with interactive rebase
- Use bisect to find a bug in minutes
- Set up a complete branch protection strategy for a team
