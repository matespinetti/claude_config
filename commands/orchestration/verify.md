---
description: Verify code quality and git state professionally
---

What to verify: $ARGUMENTS

Please verify comprehensively:

1. **Git State Verification**:
   - `git status` to see current changes
   - `git diff` to review uncommitted changes
   - `git log --oneline -5` to see recent commits
   - Ensure we're on correct branch for this work

2. **Code Quality Verification**:
   - Run project's test suite
   - Execute linting and formatting checks
   - Verify type checking (if applicable)
   - Check for any console.log or debug code

3. **Feature Verification**:
   - Test the functionality end-to-end
   - Verify edge cases and error handling
   - Check integration with existing features
   - Ensure no regressions introduced

4. **Professional Standards**:
   - Code follows project conventions
   - Appropriate documentation exists
   - Commit messages are clear and professional
   - No sensitive data or credentials in code

5. **Readiness Assessment**:
   - Is this ready for commit? (if uncommitted changes)
   - Is this ready for review? (if feature complete)
   - Are there any blockers or concerns?
   - Suggest next steps in the workflow

Provide clear feedback on what's working well and what needs attention.
