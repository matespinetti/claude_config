
---
description: Sync current branch with latest changes
---

Please help me sync this branch with the latest changes:

1. **Current State Assessment**:
   - `git status` to check working directory
   - `git branch -v` to see branch status
   - Check if we're ahead/behind develop branch

2. **Sync Strategy Decision**:
   - Determine if we should merge or rebase
   - Consider project's preferred workflow
   - Check for potential conflicts

3. **Sync Execution**:
   - Stash changes if needed: `git stash`
   - Fetch latest: `git fetch origin`
   - Sync with develop: `git rebase origin/develop` or `git merge origin/develop`
   - Apply stashed changes: `git stash pop` if applicable

4. **Conflict Resolution** (if needed):
   - Identify and explain any conflicts
   - Help resolve conflicts appropriately
   - Test after conflict resolution

5. **Verification**:
   - Ensure everything still works after sync
   - Run tests if appropriate
   - Confirm branch is properly synced

Adapt sync strategy to this project's git workflow preferences.

