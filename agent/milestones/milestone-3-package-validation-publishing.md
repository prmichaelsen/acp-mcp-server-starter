# Milestone 3: Package Validation & Publishing

**Goal**: Build example template, validate package, and publish to repository
**Duration**: 1 week
**Dependencies**: Milestone 2 (Command & Design Documentation)
**Status**: Not Started

---

## Overview

This milestone completes the package by building a working starter template example, validating all package contents, testing the installation workflow, and publishing the package to the git repository for distribution.

This ensures the package is production-ready and provides real value to users who want to quickly bootstrap MCP server projects.

---

## Deliverables

1. **Example Starter Template** (optional, for testing):
   - Minimal MCP server with hello_computer tool
   - Demonstrates all patterns in practice
   - Can be used for installation testing

2. **Package Validation**:
   - All patterns, commands, and designs validated
   - package.yaml schema compliance verified
   - README.md auto-generated content verified

3. **Installation Testing**:
   - Test local installation workflow
   - Test global installation workflow
   - Verify all files install correctly

4. **Published Package**:
   - Git tags created
   - CHANGELOG.md updated
   - Package pushed to repository
   - Installation tested from remote

---

## Success Criteria

- [ ] Example template built (if needed for testing)
- [ ] `@acp.package-validate` passes with no errors
- [ ] Local installation tested successfully
- [ ] Global installation tested successfully
- [ ] All package files install to correct locations
- [ ] Commands are discoverable and executable
- [ ] Patterns are readable and well-formatted
- [ ] CHANGELOG.md updated with release notes
- [ ] Git tag created for v1.0.0
- [ ] Package published to repository
- [ ] Remote installation tested successfully

---

## Key Files to Create/Modify

```
CHANGELOG.md (updated with v1.0.0 release notes)
package.yaml (version finalized)
README.md (final review)
```

---

## Tasks

- [Task 13](../tasks/milestone-3-package-validation-publishing/task-13-build-example-template.md): Build Example Starter Template
- [Task 14](../tasks/milestone-3-package-validation-publishing/task-14-validate-and-test.md): Validate Package and Test Installation
- [Task 15](../tasks/milestone-3-package-validation-publishing/task-15-publish-package.md): Publish Package to Repository

---

**Previous Milestone**: [Milestone 2: Command & Design Documentation](milestone-2-command-design-documentation.md)
**Next Milestone**: None (Package Complete)
**Blockers**: None
