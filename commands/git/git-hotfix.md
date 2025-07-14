---
description: Handle urgent production fixes with proper workflow
---

Urgent issue to fix: $ARGUMENTS

Please handle this production hotfix professionally:

1. **Hotfix Assessment**:
   - Confirm this requires immediate production fix
   - Understand exact issue and impact
   - Verify this can't wait for normal feature cycle

2. **Hotfix Branch Creation**:
   - Ensure we're starting from production branch (main/master)
   - `git checkout main && git pull origin main`
   - Create hotfix branch: `git checkout -b hotfix/[issue-description]`
   - Example: `hotfix/critical-login-bug` or `hotfix/security-patch`

3. **Minimal Fix Implementation**:
   - Implement the smallest possible fix
   - Focus only on the critical issue
   - Avoid any unnecessary changes or improvements
   - Test the fix thoroughly

4. **Quality Verification**:
   - Run full test suite to ensure no regressions
   - Test the specific issue is resolved
   - Verify no side effects introduced

5. **Hotfix Commit**:
   - Stage only necessary changes: `git add [specific-files]`
   - Create focused commit: `fix: resolve critical [issue description]`
   - Include any relevant issue numbers or tickets

6. **Deployment Strategy**:
   - Push hotfix branch: `git push origin hotfix/[name]`
   - Merge to main for immediate deploy: Consider fast-forward or merge
   - Plan backport to develop: Ensure fix gets into development branch
   - Tag release if needed: `git tag v1.2.1`

7. **Follow-up Actions**:
   - Create PR for review (if process allows)
   - Document the issue and fix
   - Plan any additional testing or monitoring
   - Schedule post-mortem if needed

Handle with urgency while maintaining code quality and team coordination.
