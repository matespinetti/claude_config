# /post-prp

Clean up and validate after execute-prp implementation, ensuring CLAUDE.md compliance and preparing for commit.

## Execution Flow

1. **Read CLAUDE.md**
   - Understand project standards and validation requirements
   - Check established patterns and conventions
   - Identify validation tools and testing frameworks
   - Review quality gates and compliance rules

2. **Implementation Validation**
   - Verify all PRP requirements were implemented correctly
   - Check that new features match original specifications
   - Ensure acceptance criteria from INITIAL.md are met
   - Validate no functionality was missed or incorrectly implemented

3. **CLAUDE.md Compliance Check**
   - Scan all modified/new files for 500-line limit compliance
   - Verify consistent naming conventions are followed
   - Check that modular architecture patterns are maintained
   - Ensure proper file organization and structure

4. **Code Quality Validation**
   - Run project's linter and formatter on all changed files
   - Execute type checking if project uses type annotations
   - Check for syntax errors and compilation issues
   - Validate import statements and dependencies

5. **Test Suite Validation**
   - Verify tests exist for all new functionality (expected use, edge case, failure scenario)
   - Run full test suite to ensure no regressions
   - Check test coverage meets project standards
   - Validate test files follow established patterns in /tests folder

6. **Documentation Verification**
   - Ensure new functions have proper documentation comments
   - Check complex logic has "# Reason:" explanations
   - Verify README.md updates if significant features added
   - Validate API documentation reflects changes

7. **Security and Best Practices**
   - Scan for hardcoded secrets or credentials
   - Check for common security vulnerabilities
   - Validate environment variable usage
   - Ensure error handling follows project patterns

## Validation Categories

### File Structure Compliance
```bash
# CLAUDE.md Rule Enforcement:
✓ No files exceed 500 lines
✓ Modular organization maintained
✓ Consistent naming conventions
✓ Proper import structure
✓ Files organized by feature/responsibility
```

### Test Coverage Requirements
```bash
# Required tests for new functionality:
✓ Expected use case test
✓ Edge case test  
✓ Failure scenario test
✓ Tests in /tests folder mirroring app structure
✓ All tests passing
```

### Code Quality Standards
```bash
# Project-specific validation:
✓ Linting rules pass
✓ Type checking passes (if applicable)
✓ Consistent code formatting
✓ Proper error handling
✓ No TODO/FIXME in production code
```

### Documentation Standards
```bash
# Documentation requirements:
✓ Function docstrings using project format
✓ Complex logic has explanatory comments
✓ README.md updated for significant features
✓ API changes documented
✓ No outdated documentation
```

## Smart Validation by Project Type

### Python Projects
```bash
# Validation commands:
ruff check --fix [CHANGED_FILES]
mypy [CHANGED_FILES]
pytest tests/ -v --cov=[MODULES]
bandit -r [CHANGED_FILES]

# Check for:
- PEP8 compliance
- Type hint usage
- Proper docstrings (Google style)
- Security vulnerabilities
```

### JavaScript/Node.js Projects
```bash
# Validation commands:
npm run lint [CHANGED_FILES]
npm run type-check
npm test -- --passWithNoTests --findRelatedTests [CHANGED_FILES]
npm audit --audit-level moderate

# Check for:
- ESLint rules compliance
- TypeScript compilation
- JSDoc documentation
- Dependency vulnerabilities
```

### Java Projects
```bash
# Validation commands:
./gradlew checkstyleMain spotbugsMain
./gradlew compileJava compileTestJava
./gradlew test --tests [AFFECTED_TESTS]
./gradlew dependencyCheckAnalyze

# Check for:
- Checkstyle compliance
- SpotBugs violations
- Javadoc completeness
- Security vulnerabilities
```

### Generic Validation
```bash
# Fallback validation:
[PROJECT_LINTER] [CHANGED_FILES]
[PROJECT_TYPE_CHECKER] [CHANGED_FILES]
[PROJECT_TEST_RUNNER] [AFFECTED_TESTS]
```

## Implementation vs Requirements Validation

### PRP Requirement Checklist
```bash
# Verify against original PRP:
- All specified features implemented
- Acceptance criteria met
- Integration points working
- Error handling implemented
- Performance requirements met
- Security requirements addressed
```

### INITIAL.md Alignment
```bash
# Cross-reference with original requirements:
- Core functionality delivered
- User stories satisfied
- Technical constraints respected
- Success metrics achievable
- Scope boundaries maintained
```

## Quality Gate Execution

### Critical Issues (Block Commit)
- Files exceeding 500 lines
- Failing tests
- Syntax/compilation errors
- Security vulnerabilities
- Missing required tests

### Warning Issues (Fix Recommended)
- Files approaching 400+ lines
- Code without documentation
- Complex logic without comments
- Minor linting violations
- TODO/FIXME comments

### Info Issues (Future Improvement)
- Optimization opportunities
- Refactoring suggestions
- Documentation enhancements
- Performance improvements

## Output Examples

### Successful Validation
```
🔍 Validating execute-prp implementation...

✅ PRP Requirements Verification:
   • All features from PRP implemented correctly
   • 5/5 acceptance criteria met
   • Integration points working as specified
   • Error handling properly implemented

✅ CLAUDE.md Compliance:
   • All 8 modified files under 500 lines
   • Consistent naming conventions maintained
   • Modular organization preserved
   • Proper import structure followed

✅ Code Quality:
   • Linting: All checks passed (ruff)
   • Type checking: No errors found (mypy)
   • Formatting: Code properly formatted (black)
   • Security: No vulnerabilities detected (bandit)

✅ Test Coverage:
   • 12 new tests created (4 features × 3 test types)
   • All tests passing (159/159)
   • Coverage: 87% (meets 85% requirement)
   • Tests follow established patterns

✅ Documentation:
   • 6 new functions properly documented
   • 3 complex logic blocks have "# Reason:" comments
   • README.md updated with OAuth2 setup instructions
   • API documentation reflects new endpoints

🎯 Ready for commit!
   Implementation is clean, tested, and documented.
   All quality gates passed.
```

### Issues Found - Blocking Commit
```
🔍 Validating execute-prp implementation...

❌ CRITICAL Issues (Fix Required):

📏 File Size Violations:
   • src/auth/oauth_handler.py: 547 lines (47 over limit)
   • Recommendation: Split into oauth_provider.py and oauth_validator.py

🧪 Test Failures:
   • test_user_profile.py::test_update_profile_invalid_data - FAILED
   • test_oauth.py::test_refresh_token_expired - FAILED
   • 2/161 tests failing

🔍 Code Quality Issues:
   • mypy: 3 type errors in src/auth/oauth_handler.py
   • ruff: 5 linting violations in src/user/profile.py
   • Missing docstrings for 4 new public functions

⚠️  WARNING Issues:
   
📄 Documentation Gaps:
   • Complex OAuth flow logic lacks explanatory comments
   • README.md not updated with new OAuth2 requirements
   • New API endpoints not documented

🔒 Security Concerns:
   • Potential hardcoded client secret in config.py:45
   • OAuth tokens logged in debug mode (security risk)

🛑 Commit blocked. Address critical issues first:

1. Split oauth_handler.py (over 500 lines)
2. Fix 2 failing tests
3. Resolve type errors and linting violations
4. Add missing docstrings

Then run /post-prp again to validate fixes.
```

### Partial Success with Warnings
```
🔍 Validating execute-prp implementation...

✅ Critical Checks Passed:
   • All files under 500 lines
   • All tests passing (164/164)
   • No syntax or compilation errors
   • PRP requirements fully implemented

⚠️  Warning Issues (Recommended Fixes):

📝 Documentation:
   • 2 functions missing docstrings (non-blocking)
   • Complex algorithm in calculate_oauth_signature() needs comments
   • Consider updating README with troubleshooting section

🔧 Code Quality:
   • 3 minor linting warnings (unused imports)
   • One function has 6 parameters (consider refactoring)
   • TODO comment in user_profile.py (remove before production)

📊 Test Coverage:
   • Coverage: 82% (below 85% target but above 80% minimum)
   • Consider adding integration tests for OAuth flow

✅ Ready for commit with minor improvements recommended.
   
Fix recommendations (optional):
1. Add docstrings to missing functions
2. Remove unused imports  
3. Add explanatory comment to signature calculation
4. Consider OAuth integration tests

All critical requirements met - safe to proceed with /commit.
```

### Post-Fix Validation Success
```
🔍 Re-validating after fixes...

✅ All Issues Resolved:
   • oauth_handler.py successfully split (245 + 198 lines)
   • All tests now passing (164/164)
   • Type errors fixed
   • Linting violations resolved
   • Missing docstrings added

✅ Quality Improvement:
   • Test coverage increased to 89%
   • Documentation completeness: 100%
   • Security issues addressed
   • README.md updated

🎯 Validation Complete!
   Implementation exceeds quality standards.
   Ready for commit.
   
Next steps:
   1. Run /commit for smart commit creation
   2. Consider running /docs-update for final documentation polish
```

## Integration with Workflow

### Standard PRP Flow
```bash
/generate-prp INITIAL.md    # Create implementation plan
/execute-prp PRPs/feature.md # Implement feature
/post-prp                   # Validate implementation ← You are here
/commit                     # Create quality commit
```

### Quality Gate Integration
```bash
/post-prp                   # Immediate post-implementation validation
/refactor-check            # Check for technical debt
/quality-gate              # Comprehensive pre-release validation
```

### Documentation Flow
```bash
/post-prp                   # Core validation
/docs-update               # Comprehensive documentation update
/commit                    # Final commit with all improvements
```

## Quality Checklist

The command automatically verifies:
- [ ] All PRP requirements implemented correctly
- [ ] Files comply with 500-line limit (CLAUDE.md)
- [ ] Comprehensive tests exist (expected, edge, failure cases)
- [ ] Code quality standards met (linting, types, format)
- [ ] Documentation complete and accurate
- [ ] Security best practices followed
- [ ] No regressions introduced
- [ ] Project patterns and conventions maintained

Remember: Quality validation prevents technical debt and ensures maintainable code.