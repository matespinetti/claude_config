---
description: Build features using professional git practices
---

What to build: $ARGUMENTS

Please implement this using professional development practices:

**Phase 1: Development Strategy**
1. **Review the plan**: Check existing working units for this feature
2. **Verify git state**: Ensure we're on the correct feature branch
3. **Confirm approach**: How should we handle commits for this work?

**Phase 2: Working Unit Implementation**
For each working unit:
1. **Announce the unit**: "Working on: [Unit Name] - [Goal]"
2. **Implement all tasks in unit**: Complete all TODOs for this working unit
3. **Test the unit**: Ensure this unit works as intended
4. **Quality check**: Run tests, linting, ensure it doesn't break existing code
5. **Professional commit**: Only when unit is complete and working
   - Stage relevant changes: `git add [files]`
   - Write descriptive commit: `git commit -m "[type]: [clear description]"`
   - Example: `feat: implement user authentication backend API`
6. **Unit summary**: Explain what working functionality was added

**Phase 3: Integration Verification**
After all working units:
1. **Full feature test**: Ensure entire feature works end-to-end
2. **Integration check**: Verify no regressions in existing functionality
3. **Code quality**: Final review of all changes
4. **Documentation**: Update any necessary docs
5. **Prepare for review**: Suggest next steps for feature completion

**Professional Commit Standards**:
- Only commit when functionality is complete and working
- Each commit should represent reviewable, testable changes
- Use conventional commit format: `feat:`, `fix:`, `refactor:`, `test:`, `docs:`
- Write clear, descriptive commit messages
- Test before committing to ensure builds pass

**Key Rules:**
- Never commit broken or incomplete functionality
- Each commit should tell a story of what working feature was added
- Group related changes into logical commits
- Always test before committing

This ensures every commit represents professional, working code.
