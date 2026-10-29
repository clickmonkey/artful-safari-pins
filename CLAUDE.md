## Worktrees

- Create worktrees only inside `<project-root>/.worktrees/<job>` (project root = the git repo's top folder, e.g. `~/code/marketing`). Claude Code's own `claude -w` / fix-batch lanes use `<project-root>/.claude/worktrees/<name>`; that is also inside the project root and is fine.
- Always start from the project root (`cd` there first, then `git worktree add .worktrees/<job> ...`). Never create sibling folders in `~/code` (no `~/code/<project>-wt-...`) and never put worktrees in `/tmp` or elsewhere outside the project.
- Name each worktree after its job or branch (for example `.worktrees/as-homepage-games-tile`). Keep `.worktrees/` in the repo's `.git/info/exclude`.
- When the work is pushed or merged, or the job is done, remove it: `git worktree remove <path>` then `git worktree prune` (and `git branch -d <branch>` if merged). Never `rm -rf` a worktree.
- Never remove a worktree with unpushed commits, uncommitted changes, or untracked files that matter; list it and ask instead.
