# /refactor-check

Identify refactoring opportunities across the project while maintaining functionality and following CLAUDE.md conventions.

## Execution Flow

1. **Read CLAUDE.md**
   - Understand project architecture principles and patterns
   - Check file size limits and modularity requirements
   - Identify established naming conventions and structure patterns
   - Review code organization standards

2. **File Size Analysis**
   - Scan all files for line count approaching 500-line limit
   - Identify files at 400+ lines requiring immediate attention
   - Analyze file structure to suggest logical split points
   - Detect functions or classes that could be extracted

3. **Code Duplication Detection**
   - Find repeated code patterns across files
   - Identify similar functions that could be unified
   - Detect copy-pasted code blocks needing extraction
   - Locate common utilities that should be centralized

4. **Complexity Analysis**
   - Identify functions with high complexity (nested logic, long parameter lists)
   - Find large functions that should be broken down
   - Detect deeply nested code structures
   - Analyze cognitive complexity and readability issues

5. **Architecture Pattern Recognition**
   - Compare current code organization against established patterns
   - Identify inconsistencies in module structure
   - Find opportunities to improve separation of concerns
   - Detect violations of single responsibility principle

6. **Dependency Analysis**
   - Identify circular dependencies between modules
   - Find tightly coupled components that could be decoupled
   - Detect unused imports and dependencies
   - Analyze import patterns for optimization opportunities

## Refactoring Opportunity Detection

### File Size Violations
```bash
# Check against 500-line CLAUDE.md rule
- Files at 400-499 lines: Warning (plan refactoring)
- Files at 500+ lines: Critical (immediate refactoring needed)
- Suggest logical split points based on:
  * Class boundaries
  * Function groupings
  * Feature responsibilities
  * Import dependencies
```

### Code Duplication Patterns
```python
# Example detection patterns:
# Similar function signatures
def process_user_data(user):
    # 50 lines of processing
    
def process_admin_data(admin):
    # 45 lines of similar processing
    
# Recommendation: Extract common logic to process_data_base()
```

### Complexity Indicators
```bash
# Functions needing refactoring:
- More than 20 lines
- More than 4 parameters
- Nested if/for loops > 3 levels deep
- Multiple return statements
- Mixed abstraction levels
```

### Module Organization Issues
```bash
# Architecture violations:
- Business logic in presentation layer
- Database queries in UI components  
- Mixed concerns in single modules
- Inconsistent naming patterns
- Circular import dependencies
```

## Smart Refactoring Suggestions

### File Splitting Strategies
```python
# Large file example: user_management.py (520 lines)
# Suggested split:
# → user_models.py (User class and data structures)
# → user_validation.py (Validation logic)
# → user_operations.py (CRUD operations)
# → user_auth.py (Authentication logic)
```

### Function Extraction Opportunities
```python
# Before: Complex function
def process_order(order_data):
    # 30 lines of validation
    # 25 lines of calculation
    # 20 lines of persistence
    # 15 lines of notification

# After: Extracted functions
def process_order(order_data):
    validated_data = validate_order(order_data)
    calculated_order = calculate_totals(validated_data)
    saved_order = save_order(calculated_order)
    send_notifications(saved_order)
    return saved_order
```

### Common Pattern Extraction
```python
# Detected pattern across multiple files:
# API response formatting repeated 8 times
# Recommendation: Create response_formatter.py utility
def format_api_response(data, status='success', message=None):
    return {
        'status': status,
        'data': data,
        'message': message,
        'timestamp': datetime.utcnow().isoformat()
    }
```

## Refactoring Priority Levels

### Critical (Immediate Action Required)
- Files exceeding 500 lines
- Circular dependencies
- Security-related code duplication
- Functions with > 50 lines

### High Priority (Plan for Next Sprint)
- Files at 400-499 lines
- Functions with > 20 lines
- Significant code duplication (>10 occurrences)
- Complex nested logic (>3 levels)

### Medium Priority (Technical Debt)
- Inconsistent naming patterns
- Minor code duplication (3-10 occurrences)
- Suboptimal module organization
- Functions with >4 parameters

### Low Priority (Optimization)
- Unused imports
- Minor complexity issues
- Style inconsistencies
- Documentation improvements

## Safe Refactoring Guidelines

### Preserve Functionality
```bash
# Never change behavior during refactoring:
- Extract methods without modifying logic
- Move code without altering execution flow
- Rename for clarity without functional changes
- Split files while maintaining interfaces
```

### Maintain Test Coverage
```bash
# Ensure refactoring doesn't break tests:
- Run full test suite before refactoring
- Update import statements in tests
- Verify all tests pass after changes
- Add tests for new extracted modules
```

### Follow CLAUDE.md Rules
```bash
# Adhere to established conventions:
- Keep all files under 500 lines
- Follow project naming patterns
- Maintain consistent import structure
- Preserve architectural patterns
```

## Output Examples

### Comprehensive Refactoring Report
```
🔍 Analyzing codebase for refactoring opportunities...

⚠️  CRITICAL Issues (Immediate Action Required):
📁 src/user_management.py - 547 lines (47 lines over limit)
   → Suggested split:
     • user_models.py (User, Profile classes - 120 lines)
     • user_validation.py (Validation logic - 95 lines)  
     • user_operations.py (CRUD operations - 180 lines)
     • user_auth.py (Authentication - 152 lines)

📁 src/api/endpoints.py - 523 lines (23 lines over limit)
   → Suggested split by feature:
     • auth_endpoints.py (Authentication routes - 145 lines)
     • user_endpoints.py (User management - 178 lines)
     • admin_endpoints.py (Admin functions - 200 lines)

🔴 HIGH Priority Issues:
📄 src/utils/helpers.py - 487 lines (approaching limit)
   → Extract database utilities to separate module

🔄 Code Duplication Found:
   • API response formatting (8 occurrences across 5 files)
     → Create shared response_formatter.py utility
   • User validation logic (4 similar functions)
     → Extract to validation_base.py
   • Database connection setup (6 files)
     → Centralize in db_connection.py

⚡ Complexity Issues:
   • process_payment() - 67 lines, 8 parameters
     → Split into validate_payment(), calculate_fees(), execute_payment()
   • generate_report() - 45 lines, nested 4 levels deep
     → Extract data_aggregation() and format_output()

🏗️  Architecture Recommendations:
   • Move business logic from controllers to service layer
   • Extract common interfaces for data repositories
   • Separate API models from database models
   • Create shared exception handling utilities

📊 Summary:
   • 2 files over 500-line limit (CRITICAL)
   • 1 file approaching limit (HIGH)
   • 4 duplication patterns found
   • 8 complex functions identified
   • 12 architectural improvements suggested

🎯 Recommended Action Plan:
   1. Split user_management.py immediately
   2. Split api/endpoints.py by feature
   3. Extract common utilities (response formatting, validation)
   4. Refactor complex functions (process_payment, generate_report)
   5. Improve overall architecture separation
```

### Quick Status Check
```
🔍 Quick refactoring scan...

✅ File Size Compliance:
   • All files under 500 lines
   • 2 files approaching limit (400+ lines)

✅ Code Quality:
   • No critical duplication found
   • 3 functions could be simplified
   • Architecture follows established patterns

📋 Minor Improvements Available:
   • Extract 2 utility functions
   • Simplify nested logic in search_users()
   • Consider splitting large_data_processor.py (445 lines)

🎯 Overall Status: GOOD
   No immediate refactoring required.
```

### Post-Refactoring Validation
```
🔍 Validating recent refactoring changes...

✅ File Size Compliance:
   • user_management.py split successfully
   • All new files under 500 lines
   • No violations detected

✅ Functionality Preserved:
   • All tests passing (147/147)
   • Import statements updated correctly
   • API responses unchanged

✅ Code Quality Improved:
   • Duplication reduced from 8 to 0 occurrences
   • Average function complexity decreased 40%
   • Module separation improved

🎯 Refactoring Success:
   Technical debt reduced significantly.
   Codebase maintainability improved.
```

## Integration with Development Workflow

### Before Major Features
```bash
/refactor-check      # Identify technical debt
# Address critical issues before new development
/generate-prp        # Create feature requirements
/execute-prp         # Implement feature
```

### Regular Maintenance
```bash
/refactor-check      # Weekly code health assessment
# Plan refactoring tasks
# Address issues incrementally
```

### Pre-Release Quality Gates
```bash
/refactor-check      # Ensure code quality standards
/quality-gate        # Comprehensive validation
/commit              # Clean, maintainable code
```

## Quality Checklist

The command automatically evaluates:
- [ ] All files comply with 500-line limit
- [ ] No critical code duplication exists
- [ ] Function complexity is manageable
- [ ] Module organization follows patterns
- [ ] No circular dependencies present
- [ ] Architecture separation is maintained
- [ ] Refactoring opportunities are prioritized

Remember: Refactoring improves maintainability without changing functionality.