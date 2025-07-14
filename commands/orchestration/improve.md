---
description: Improve code with professional git practices
---

What to improve: $ARGUMENTS

Please improve this systematically:

1. **Current State Analysis**:
   - Understand current implementation and its history
   - `git log --oneline [file]` to see evolution if relevant
   - Identify specific improvement opportunities

2. **Improvement Strategy**:
   - Determine if this should be separate refactor branch or part of feature
   - Plan improvements that don't change external behavior
   - Consider impact on existing functionality

3. **Professional Implementation**:
   - Make improvements incrementally
   - Test after each significant change
   - Ensure refactoring doesn't break functionality
   - Follow project patterns and conventions

4. **Quality Verification**:
   - Run tests to ensure no behavioral changes
   - Verify performance improvements (if applicable)
   - Check that code is more maintainable

5. **Professional Commit**:
   - Stage changes: `git add [files]`
   - Create focused commit: `refactor: [clear description of improvement]`
   - Example: `refactor: optimize database queries in user service`

6. **Documentation**:
   - Update comments if behavior is clearer
   - Note any performance improvements
   - Suggest any follow-up improvements

Focus on improvements that provide real value while maintaining reliability.
