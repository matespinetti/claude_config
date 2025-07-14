---
description: Prepare code for production release
---

Release to prepare: $ARGUMENTS

Please prepare this code for production release:

1. **Release Readiness Check**:
   - Verify all planned features are complete and merged
   - `git status` to ensure clean working directory
   - Confirm we're on develop branch with latest changes

2. **Quality Assurance**:
   - Run complete test suite: all tests passing
   - Execute security scans if available
   - Verify performance benchmarks
   - Check for any remaining TODOs or debug code

3. **Version Management**:
   - Determine appropriate version number (semantic versioning)
   - Update version in package.json, setup.py, or relevant files
   - Update CHANGELOG.md with new features, fixes, and breaking changes
   - Update documentation with any API changes

4. **Release Branch Creation**:
   - Create release branch: `git checkout -b release/v[version]`
   - Example: `git checkout -b release/v1.2.0`
   - Commit version updates: `git commit -m "chore: bump version to v1.2.0"`

5. **Final Testing**:
   - Run full regression test suite
   - Execute integration tests
   - Perform any manual testing required
   - Verify deployment scripts work correctly

6. **Release Documentation**:
   - Generate release notes from commit history
   - Document any migration steps required
   - Update README with new features or changes
   - Prepare deployment instructions

7. **Release Execution**:
   - Merge release branch to main: `git checkout main && git merge release/v[version]`
   - Create release tag: `git tag -a v[version] -m "Release version [version]"`
   - Push main and tags: `git push origin main --tags`
   - Merge back to develop: `git checkout develop && git merge main`

8. **Post-Release**:
   - Deploy to production environment
   - Monitor for any immediate issues
   - Clean up release branch: `git branch -d release/v[version]`
   - Update issue tracker with released features

Ensure thorough preparation for stable production deployment.
