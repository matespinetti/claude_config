---
description: Prepare code for review with comprehensive checks
---

Please prepare this code for professional review:

1. **Git History Analysis**:
   - `git log --oneline -10` to review recent commits
   - Check for WIP commits, unclear messages, or redundant commits
   - Assess if commit history tells a clear story

2. **Code Quality Verification**:
   - `git status` to see any uncommitted changes
   - `git diff` and `git diff --staged` to review changes
   - Run linting: execute project's lint command
   - Run tests: execute full test suite
   - Check for debugging code, console.logs, or TODOs

3. **Professional Standards Check**:
   - Verify commit messages follow conventional format
   - Ensure each commit represents working functionality
   - Check that sensitive data isn't included
   - Verify documentation is updated

4. **Git Cleanup Recommendations**:
   - Suggest squashing related commits if needed
   - Recommend improving commit messages
   - Propose organizing commits more logically
   - Consider interactive rebase if beneficial

5. **Review Preparation**:
   - Generate summary of all changes made
   - Identify areas needing special reviewer attention
   - Suggest testing instructions for reviewers
   - Check for security or performance implications

6. **Final Git Status**:
   - Confirm working directory is clean
   - Show final commit history: `git log --oneline -5`
   - Verify branch is ready for merge/PR

Provide specific git commands and recommendations for review readiness.
