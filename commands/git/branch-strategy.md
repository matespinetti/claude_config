# /branch-strategy

## Argument: $ARGUMENTS

Manage GitOps branch workflow and transitions following main → development → feature branch strategy.

## Execution Flow

1. **Read CLAUDE.md**
   - Understand project branching conventions and naming patterns
   - Check established GitOps workflow rules
   - Identify branch protection and validation requirements
   - Review integration and deployment standards

2. **Current Branch Detection**
   - Identify current branch and position in GitOps flow
   - Check git status and working directory state
   - Validate branch naming follows project conventions
   - Determine available workflow actions

3. **Branch State Analysis**
   - Check for uncommitted changes
   - Verify branch is up to date with remote
   - Analyze branch relationships (upstream/downstream)
   - Identify merge conflicts or integration issues

4. **Argument Analysis & Operation Selection**
   - Parse $ARGUMENTS to determine intended operation
   - Execute appropriate branch operation based on argument
   - Handle different argument types (branch names, operations, status)
   - Provide contextual help for invalid or ambiguous arguments

## Argument-Based Operations

### Create Feature Branch
```bash
/branch-strategy feature/oauth-integration

# Auto-detects: Creating new feature branch
# Execution:
1. Validate currently on development branch
2. Pull latest changes from origin/development
3. Create new feature branch: feature/oauth-integration
4. Set up tracking with remote repository
5. Update TASK.md with branch information
6. Create initial commit marking branch creation
```

### Create Hotfix Branch
```bash
/branch-strategy hotfix/critical-security-fix

# Auto-detects: Creating new hotfix branch
# Execution:
1. Validate currently on main/production branch
2. Pull latest changes from origin/main
3. Create hotfix branch for emergency fixes
4. Set up expedited workflow tracking
5. Document emergency change process
```

### Switch to Existing Branch
```bash
/branch-strategy development
/branch-strategy main
/branch-strategy feature/existing-feature

# Auto-detects: Switching to existing branch
# Execution:
1. Stash any uncommitted changes safely
2. Switch to target branch
3. Pull latest changes from remote
4. Restore stashed changes if applicable
5. Update working directory context
```

### Workflow Operations
```bash
/branch-strategy prep-integration

# Auto-detects: Prepare current feature for integration
# Execution:
1. Validate feature implementation complete
2. Rebase on latest development branch
3. Resolve any merge conflicts
4. Run integration validation tests
5. Prepare merge commit message
6. Generate PR template with context
```

```bash
/branch-strategy prep-release

# Auto-detects: Prepare development for release
# Execution:
1. Validate all features ready for production
2. Generate release notes and changelog
3. Bump version numbers appropriately
4. Create release branch if needed
5. Prepare production deployment artifacts
```

### Status and Help
```bash
/branch-strategy status

# Auto-detects: Show current branch status
# Shows complete branch health report

/branch-strategy help

# Auto-detects: Show available operations
# Lists all possible arguments and usage
```

## Smart Argument Detection

### Automatic Operation Recognition
```bash
# Feature branch creation (starts with "feature/"):
/branch-strategy feature/oauth-integration
/branch-strategy feature/user-dashboard
/branch-strategy feature/payment-system

# Hotfix branch creation (starts with "hotfix/"):
/branch-strategy hotfix/security-vulnerability
/branch-strategy hotfix/payment-gateway-fix

# Existing branch switching (matches existing branch names):
/branch-strategy development
/branch-strategy main
/branch-strategy feature/existing-branch

# Workflow operations (predefined commands):
/branch-strategy prep-integration
/branch-strategy prep-release
/branch-strategy status
/branch-strategy help
```

### Argument Validation
```bash
# Valid patterns:
feature/* → Create new feature branch
hotfix/* → Create new hotfix branch
[existing-branch] → Switch to existing branch
prep-integration → Prepare feature for development merge
prep-release → Prepare development for production
status → Show current branch status
help → Show usage information

# Invalid patterns trigger help:
/branch-strategy invalid-pattern
# → Shows usage help and suggests valid options
```

## Smart Branch Operations

### Automatic Conflict Resolution
```bash
# When rebasing on development:
🔄 Rebasing feature/oauth-integration on development...

✅ No conflicts detected
✅ Feature branch updated with latest development
✅ All commits preserved
✅ Ready for integration

# If conflicts found:
⚠️  Merge conflicts detected:
- src/auth/handlers.py (conflict in import statements)
- tests/test_auth.py (conflict in test setup)

🛠️  Conflict resolution required:
1. Review conflicted files
2. Resolve conflicts manually
3. Run /post-prp to validate resolution
4. Continue with prep-integration
```

### Branch Health Monitoring
```bash
# Check branch status:
/branch-strategy status

📊 Branch Health Report:
✅ Current: feature/oauth-integration
✅ Up to date with origin/feature/oauth-integration
✅ 5 commits ahead of development
✅ No merge conflicts with development
✅ All commits follow conventional format

📋 Integration readiness:
- Feature implementation: Complete
- Tests coverage: 89% (above 85% requirement)
- Documentation: Updated
- Code quality: All checks pass

🎯 Ready for: prep-integration
```

## Output Examples

### Feature Branch Creation
```bash
/branch-strategy feature/user-dashboard

🌿 Creating feature branch...

✅ Branch setup complete:
- Current branch: feature/user-dashboard
- Base branch: development (up to date)
- Tracking: origin/feature/user-dashboard
- Initial commit: feat: initialize user dashboard feature branch

📋 Feature development ready:
- TASK.md updated with branch information
- Ready for INITIAL.md editing
- Next steps: /generate-prp INITIAL.md

🎯 Branch: feature/user-dashboard
   From: development
   Status: Ready for feature development
```

### Branch Switching
```bash
/branch-strategy development

🔄 Switching to development branch...

✅ Branch switch complete:
- Stashed 3 uncommitted changes safely
- Switched to: development
- Pulled latest changes (2 new commits)
- Restored stashed changes

📊 Development branch status:
- Up to date with origin/development
- 3 feature branches ready for integration
- Last update: 2 hours ago

🎯 Current: development
   Available features for integration:
   - feature/oauth-integration (ready)
   - feature/user-profiles (in progress)
   - feature/admin-dashboard (ready)
```

### Integration Preparation
```bash
/branch-strategy prep-integration

🔄 Preparing integration with development...

✅ Pre-integration validation:
- Feature implementation complete
- All tests passing (47/47)
- Documentation updated
- Code quality standards met

🔄 Branch synchronization:
- Rebased on latest development (no conflicts)
- Feature commits preserved and cleaned
- Integration tests prepared

📝 PR preparation:
- Title: feat(auth): add OAuth2 Google integration
- Description: Generated from PRP requirements
- Checklist: All items completed
- Reviewers: Suggested based on changed files

🎯 Ready for merge request:
   feature/user-dashboard → development
   
Next steps:
1. Create PR in repository UI
2. Wait for CI/CD validation
3. Address any review feedback
4. Merge when approved
```

### Hotfix Creation
```bash
/branch-strategy hotfix/payment-gateway-timeout

🚨 Creating emergency hotfix branch...

✅ Hotfix setup complete:
- Current branch: hotfix/payment-gateway-timeout
- Base branch: main (latest production)
- Priority: Emergency fix
- Tracking: origin/hotfix/payment-gateway-timeout

⚡ Expedited workflow activated:
- Minimal validation requirements
- Fast-track testing approach
- Direct-to-production path available

📋 Hotfix development ready:
- Focus on minimal, targeted fix
- Comprehensive testing still required
- Document fix thoroughly

🎯 Branch: hotfix/payment-gateway-timeout
   From: main
   Status: Emergency fix mode
```

### Status Check
```bash
/branch-strategy status

📊 Current Branch Status:

🌿 Branch: feature/oauth-integration
📍 Position: 5 commits ahead of development
🔄 Sync: Up to date with origin
📈 Progress: Feature implementation complete

✅ Quality metrics:
- Code quality: All checks pass
- Test coverage: 91% (target: 85%)
- Documentation: Complete
- Security: No issues

📋 Workflow status:
- PRP executed: ✅ 
- Post-PRP validation: ✅
- Ready for integration: ✅

🎯 Next recommended action: prep-integration

Available actions:
- /branch-strategy prep-integration
- /branch-strategy development
- /branch-strategy main
```

### Help and Usage
```bash
/branch-strategy help

📖 Branch Strategy Usage:

🌿 Create branches:
- /branch-strategy feature/branch-name
- /branch-strategy hotfix/issue-name

🔄 Switch branches:
- /branch-strategy development
- /branch-strategy main
- /branch-strategy feature/existing-branch

⚡ Workflow operations:
- /branch-strategy prep-integration
- /branch-strategy prep-release
- /branch-strategy status

📋 Examples:
- /branch-strategy feature/oauth-integration
- /branch-strategy prep-integration
- /branch-strategy development
- /branch-strategy status

🎯 Current context: feature/oauth-integration
   Suggested next action: prep-integration
```

## Integration with Development Workflow

### Standard Feature Flow
```bash
# Complete feature development cycle:
/branch-strategy feature/new-feature
# Edit INITIAL.md, then:
/generate-prp INITIAL.md
/execute-prp PRPs/new-feature.md
/post-prp
/commit
/branch-strategy prep-integration
# Create PR via repository UI
```

### Emergency Hotfix Flow
```bash
# Critical production fix:
/branch-strategy hotfix/critical-issue
# Implement minimal fix, then:
/post-prp --hotfix-mode
/commit
/branch-strategy prep-release --hotfix
# Fast-track to production
```

### Branch Management Flow
```bash
# Check current status:
/branch-strategy status

# Switch between branches:
/branch-strategy development
/branch-strategy main
/branch-strategy feature/existing-feature

# Prepare for integration/release:
/branch-strategy prep-integration
/branch-strategy prep-release
```

## Quality Checklist

The command automatically manages:
- [ ] Proper branch naming conventions
- [ ] Clean branch history and relationships
- [ ] Up-to-date synchronization with remotes
- [ ] Conflict resolution and validation
- [ ] Integration readiness assessment
- [ ] Release preparation and validation
- [ ] Emergency hotfix workflow support
- [ ] GitOps compliance throughout

Remember: Proper branch strategy ensures safe, systematic feature delivery.