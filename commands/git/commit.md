# Commit

Automate the commit process following best practices with conventional commits, validation, and quality checks. Analyzes staged files and project configuration to determine the best approach automatically.

## Project Analysis & Detection

1. **Project Type Detection**
   - Check for package.json, requirements.txt, Cargo.toml, pom.xml, etc.
   - Identify framework (React, Django, Express, Spring, etc.)
   - Detect testing framework and linting tools
   - Read project configuration files for validation commands

2. **Staged Files Analysis**
   - Group files by logical purpose and commit type
   - Extract scope from file paths and project structure
   - Detect breaking changes in APIs or configurations
   - Identify if documentation needs updating
   - Determine if changes should be split into multiple commits

## Smart Commit Splitting

### Detection Logic

**Group files by commit type:**
- **Features**: New files, major functionality additions
- **Fixes**: Bug fixes, error handling improvements
- **Docs**: README, documentation, comments
- **Tests**: Test files, test utilities
- **Chore**: Dependencies, configuration, build files
- **Refactor**: Code restructuring without behavior changes
- **Style**: Formatting, linting fixes

**Split triggers:**
- Files in different feature directories (e.g., `auth/` + `user/`)
- Mixed commit types (feature + fix + docs)
- Unrelated functionality changes
- Large changesets spanning multiple modules

### Grouping Examples

```bash
# Example 1: Mixed changes
src/auth/login.py     → feat(auth): OAuth2 login
src/user/profile.py   → fix(user): validation bug
docs/api.md          → docs: update auth endpoints

# Example 2: Multiple features  
src/auth/           → feat(auth): add OAuth2
src/payments/       → feat(payments): add Stripe integration
tests/             → test: add tests for auth and payments

# Example 3: Refactor + feature
src/utils/helpers.py → refactor(utils): extract common functions
src/auth/new_flow.py → feat(auth): add 2FA support
```

## Commit Message Generation

### Automatic Analysis
- Analyze staged changes to determine commit type
- Extract affected scope from modified files
- Detect breaking changes in API signatures
- Generate descriptive commit message

### Conventional Commit Format
```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Supported Types
- **feat**: New feature
- **fix**: Bug fix
- **docs**: Documentation changes
- **style**: Code style changes (formatting, etc.)
- **refactor**: Code refactoring
- **test**: Adding or updating tests
- **chore**: Maintenance tasks
- **perf**: Performance improvements
- **ci**: CI/CD changes
- **build**: Build system changes

### Smart Detection Rules
```bash
# Detect type based on file patterns:
- New files in features/ → feat
- Changes in tests/ → test
- README/docs changes → docs
- Package.json/requirements.txt → build
- .github/workflows → ci
- Bug fix keywords in files → fix
```

## Execution Flow

1. **Pre-Validation**
   ```bash
   # Check if files are staged
   if [ -z "$(git diff --cached --name-only)" ]; then
     echo "No files staged. Please stage files first with 'git add'"
     exit 1
   fi
   ```

2. **Project Detection & Configuration**
   - Automatically detect project type and tech stack
   - Load appropriate validation commands from project config
   - Determine testing strategy based on project structure

3. **Smart Analysis & Grouping**
   - Analyze staged files for logical groupings
   - Detect mixed commit types or unrelated changes
   - Suggest commit splitting if needed
   - Present grouping strategy to user for approval

4. **Quality Gate Execution** (for each commit group)
   - Run linting and formatting for relevant files
   - Execute type checking if configured
   - Run tests related to changed files in group
   - Scan for security issues and secrets

5. **Commit Generation & Execution**
   - Generate conventional commit message for each group
   - Present all proposed commits for review
   - Execute commits sequentially if approved
   - Provide rollback option if any commit fails

## Configuration Examples

### For Python Projects
```bash
# Quality checks
ruff check --fix $(git diff --cached --name-only --diff-filter=AM | grep "\.py$")
mypy $(git diff --cached --name-only --diff-filter=AM | grep "\.py$")

# Tests
uv run pytest tests/ -v --cov-fail-under=80

# Security
bandit -r $(git diff --cached --name-only --diff-filter=AM | grep "\.py$")
```

### For JavaScript/Node.js Projects
```bash
# Quality checks
npm run lint $(git diff --cached --name-only --diff-filter=AM | grep -E "\.(js|ts|jsx|tsx)$")
npm run type-check

# Tests
npm test -- --passWithNoTests --findRelatedTests $(git diff --cached --name-only)

# Security
npm audit --audit-level moderate
```

### For Java Projects
```bash
# Quality checks
./gradlew checkstyleMain spotbugsMain

# Tests
./gradlew test --tests $(affected_test_classes)

# Security
./gradlew dependencyCheckAnalyze
```

### Generic Fallback
```bash
# Quality checks
[PROJECT_LINTER] [STAGED_FILES]
[PROJECT_TYPE_CHECKER] [STAGED_FILES]

# Tests
[PROJECT_TEST_RUNNER] --related [STAGED_FILES]
```

## Advanced Features

### Breaking Change Detection
```bash
# Detect API changes
- Public method signature changes
- Removed public methods/classes
- Changed configuration schema
- Database migration files
```

### Scope Auto-Detection
```bash
# Extract scope from file paths
src/auth/ → auth
components/ui/ → ui
api/users/ → users
docs/ → docs
```

### Commit Hooks Integration
```bash
# Update .git/hooks/pre-commit
#!/bin/bash
exec smart-commit --validate-only
```

## Command Output Examples

### Single Focused Commit
```
🔍 Analyzing project: Node.js + TypeScript + React
📁 Staged files: 3 files in src/components/auth/

✅ ESLint passed
✅ TypeScript compilation passed  
✅ Tests passed (2 new, 0 failed)
✅ No security issues found

📝 Generated commit message:
feat(auth): add OAuth2 login component

- Add GoogleLoginButton component
- Implement OAuth2 flow with redirect handling
- Add loading states and error handling
- Update auth context with Google provider

Commit this message? (y/n): y

🎯 Committing...
[main 1a2b3c4] feat(auth): add OAuth2 login component
 3 files changed, 89 insertions(+), 5 deletions(-)
```

### Smart Split Suggestion
```
🔍 Analyzing project: Python + Django + pytest
📁 Staged files: 8 files across multiple areas

⚠️  Detected multiple commit types. Recommended split:

📦 Commit 1: feat(auth): add OAuth2 integration
  • src/auth/oauth.py (new)
  • src/auth/providers.py (new)
  • src/settings.py (modified)

🐛 Commit 2: fix(user): resolve profile validation bug  
  • src/user/models.py (modified)
  • src/user/forms.py (modified)

📝 Commit 3: docs: update authentication guide
  • docs/auth.md (modified)
  • README.md (modified)

🧪 Commit 4: test: add comprehensive auth tests
  • tests/test_oauth.py (new)
  • tests/test_user_profile.py (modified)

Proceed with split? (Y/n): y

✅ Running validation for each commit group...

🎯 Executing commits:
[main 1a2b3c4] feat(auth): add OAuth2 integration
[main 2b3c4d5] fix(user): resolve profile validation bug
[main 3c4d5e6] docs: update authentication guide  
[main 4d5e6f7] test: add comprehensive auth tests

✨ Successfully created 4 focused commits!
```

### Mixed Changes with User Choice
```
🔍 Analyzing project: React + TypeScript

⚠️  Mixed changes detected:
  • Feature: New dashboard component (3 files)
  • Fix: Button styling issue (2 files)  
  • Chore: Update dependencies (1 file)

Options:
1. Split into 3 focused commits (recommended)
2. Group feature + fix, separate chore
3. Single commit with mixed scope

Choose option (1-3): 1

✅ Proceeding with 3 focused commits...
```

## Quality Checklist

The command automatically verifies:
- [ ] All staged files pass project linting rules
- [ ] Type checking passes (if configured)  
- [ ] Related tests pass
- [ ] No secrets or credentials in staged code
- [ ] Commit message follows conventional format
- [ ] Breaking changes are detected and marked
- [ ] Documentation updated for significant changes

Remember: This command learns from your project structure and adapts to your team's workflow.