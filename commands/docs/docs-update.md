# /docs-update

Update all documentation to reflect current codebase state following CLAUDE.md standards.

## Execution Flow

1. **Read CLAUDE.md**
   - Understand project documentation standards and conventions
   - Identify required documentation formats and patterns
   - Check documentation requirements for the project type

2. **Analyze Recent Changes**
   - Scan git commits since last documentation update
   - Identify new features, API changes, and functionality additions
   - Detect configuration changes and setup requirement updates
   - Find breaking changes that need documentation

3. **Codebase Documentation Analysis**
   - Scan for functions/classes missing documentation comments
   - Identify complex logic lacking "# Reason:" explanations
   - Check for outdated inline comments
   - Validate documentation format matches project standards

4. **README.md Updates**
   - Add new features to feature list
   - Update installation/setup instructions for new dependencies
   - Refresh usage examples with new functionality
   - Update API endpoints or configuration options
   - Ensure getting started guide reflects current state

5. **API Documentation Generation**
   - Extract function signatures and docstrings
   - Generate endpoint documentation for APIs
   - Create parameter and return value documentation
   - Update schema definitions and examples
   - Maintain consistent documentation format

6. **Examples Folder Updates**
   - Add examples for new features and patterns
   - Update existing examples with current best practices
   - Remove outdated or deprecated examples
   - Ensure examples follow current project conventions
   - Document usage patterns discovered during development

7. **Inline Code Documentation**
   - Add missing function/class documentation using project standard format
   - Insert "# Reason:" comments for complex business logic
   - Update outdated comments that no longer match code
   - Remove redundant or obvious comments
   - Ensure non-obvious code is well-explained

## Smart Documentation Detection

### New Features Requiring Documentation
```bash
# Detect patterns that need docs:
- New public functions/classes
- New API endpoints
- New configuration options
- New dependencies or setup steps
- Changes to existing public interfaces
```

### Documentation Format by Language
```bash
# Python: Google/Sphinx style docstrings
def example_function(param1: str) -> bool:
    """
    Brief description of what the function does.
    
    Args:
        param1 (str): Description of the parameter.
        
    Returns:
        bool: Description of what is returned.
        
    Raises:
        ValueError: When param1 is invalid.
    """

# JavaScript: JSDoc format  
/**
 * Brief description of what the function does.
 * @param {string} param1 - Description of the parameter
 * @returns {boolean} Description of what is returned
 * @throws {Error} When param1 is invalid
 */

# Other languages: Follow project's established format
```

### Complex Logic Documentation
```python
# Example of "# Reason:" comments for non-obvious code
if user.role == 'admin' and time.hour < 6:
    # Reason: Admin maintenance window is 12am-6am to avoid user impact
    allow_maintenance_operations = True
```

## Documentation Updates by Category

### README.md Sections to Update
- **Installation**: New dependencies, environment requirements
- **Features**: New functionality and capabilities  
- **Usage**: Updated examples and code snippets
- **API Reference**: New endpoints, parameters, responses
- **Configuration**: New settings and environment variables
- **Troubleshooting**: Common issues with new features

### API Documentation Updates
- **Endpoint Documentation**: New routes and methods
- **Request/Response Examples**: Current data formats
- **Authentication**: Updated auth requirements
- **Error Codes**: New error responses
- **Rate Limiting**: Updated limits and policies

### Code Documentation Updates
- **Function Documentation**: All public methods and classes
- **Complex Logic**: Business rules and algorithms
- **Configuration**: Setup and deployment instructions
- **Architecture**: High-level system design updates

## Validation and Quality Checks

### Documentation Quality Gates
- All public functions have proper documentation
- Complex logic has explanatory comments
- README.md reflects current functionality
- Examples work with current codebase
- No broken links or outdated references
- Documentation follows established format standards

### Automated Checks
```bash
# Check for missing documentation
- Functions without docstrings
- Classes without descriptions  
- Complex logic without comments
- New features not in README

# Validate documentation quality
- Proper format for docstrings
- Consistent style across project
- Working code examples
- Up-to-date dependency lists
```

## Output Examples

### Successful Documentation Update
```
🔍 Analyzing project documentation needs...

📖 Documentation updates found:
  • 3 new functions need docstrings
  • README.md missing 2 new features
  • 5 complex code blocks need "# Reason:" comments
  • examples/ folder needs OAuth2 integration example

✅ Updates completed:
  • Added docstrings to src/auth/oauth.py (3 functions)
  • Updated README.md with OAuth2 and profile features
  • Added explanatory comments to user validation logic
  • Created examples/oauth2_integration.py
  • Updated API documentation with new endpoints

📋 Documentation summary:
  • README.md: Added OAuth2 setup instructions and usage
  • API docs: 4 new endpoints documented
  • Code comments: 5 complex logic blocks explained
  • Examples: 1 new integration example added

✨ All documentation updated and validated!
```

### Comprehensive Update Report
```
🔍 Scanning codebase for documentation needs...

📊 Analysis results:
  • Git commits: 12 commits since last docs update
  • New features: OAuth2 integration, user profiles, admin dashboard
  • API changes: 6 new endpoints, 2 modified responses
  • Dependencies: Added 3 new packages
  
🚀 Updates applied:

📄 README.md updates:
  • Installation: Added OAuth2 client setup steps
  • Features: Added user profile management section
  • Configuration: New environment variables documented
  • Troubleshooting: Common OAuth2 setup issues

🔧 API Documentation:
  • POST /auth/oauth2/login - OAuth2 authentication
  • GET /users/profile - User profile retrieval
  • PUT /users/profile - Profile updates
  • GET /admin/dashboard - Admin analytics

💻 Code Documentation:
  • src/auth/oauth.py: 3 functions documented
  • src/users/profile.py: 2 classes documented  
  • src/admin/analytics.py: Complex query logic explained

📁 Examples Updated:
  • examples/oauth2_setup.py - Complete OAuth2 integration
  • examples/profile_management.py - User profile operations
  • Updated existing examples to use new patterns

✅ Quality validation passed:
  • All public functions documented
  • Complex logic has explanations
  • Examples tested and working
  • No broken links found
```

## Quality Checklist

The command automatically verifies:
- [ ] All new public functions have proper documentation
- [ ] Complex business logic has "# Reason:" explanations  
- [ ] README.md includes all new features and setup steps
- [ ] API documentation reflects current endpoints
- [ ] Examples folder has working code for new features
- [ ] Documentation follows project's established format
- [ ] No outdated or broken references remain

Remember: Good documentation enables team collaboration and project maintainability.