---
description: Start a new feature following professional git workflow
---

Feature to start: $ARGUMENTS

Please set up a new feature with professional git workflow:

1. **Pre-Flight Checks**:
   - `git status` to ensure clean working directory
   - Check current branch (should be develop or main)
   - `git pull origin develop` to get latest changes
   - Warn if there are uncommitted changes

2. **Feature Branch Creation**:
   - Create descriptive branch name following project conventions
   - Typically: `feature/[feature-name]` or `feat/[feature-name]`
   - Examples: `feature/user-authentication`, `feature/payment-integration`
   - Execute: `git checkout -b feature/[name]`

3. **Initial Setup**:
   - Push branch for backup: `git push -u origin feature/[name]`
   - Consider any initial scaffolding or setup needed
   - Update CLAUDE.md if this is a major feature addition

4. **Development Readiness**:
   - Confirm git setup is ready for development
   - Explain the workflow for this feature:
     * Development will happen on this branch
     * Commits will be made at logical working points
     * Feature will be merged back to develop when complete
   - Suggest next step: `/plan [feature]` to break down the work

**Important**: This creates a clean, isolated environment for feature development following professional git practices.
