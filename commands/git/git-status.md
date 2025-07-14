---
description: Get comprehensive git repository status and health check
---

Please provide a comprehensive git repository status:

1. **Current State Overview**:
   - `git status` - current branch and working directory state
   - `git branch -v` - all branches with latest commit info
   - `git remote -v` - configured remotes
   - Show any uncommitted changes or untracked files

2. **Commit History Analysis**:
   - `git log --oneline -10` - recent commit history
   - Check for any WIP commits or unclear messages
   - Identify any merge commits or complex history

3. **Branch Relationship**:
   - Compare with main/develop: `git rev-list --count main..HEAD`
   - Check if branch is ahead/behind: `git status -uno`
   - Identify any diverged branches

4. **Repository Health**:
   - Check for any large files or binary commits
   - Verify .gitignore is working properly
   - Look for any security concerns (credentials, keys)
   - Check if dependencies need updates

5. **Workflow Recommendations**:
   - Suggest any needed git cleanup
   - Recommend if sync with remote is needed
   - Identify if any branches can be cleaned up
   - Propose any workflow improvements

6. **Next Steps Suggestion**:
   - Based on current state, what should be done next?
   - Any pending work or incomplete features?
   - Recommend appropriate commands for current situation

Provide clear, actionable insights about the repository state.
