# Task 14: Validate Package and Test Installation

**Milestone**: M3 - Package Validation & Publishing
**Estimated Time**: 2-3 hours
**Dependencies**: Task 13 (Example Template) - Optional
**Status**: Not Started

---

## Objective

Validate the package contents, test local and global installation workflows, and ensure all files install correctly to user projects.

---

## Context

Package validation ensures:
- All patterns, commands, and designs are valid
- package.yaml schema compliance
- README.md auto-generated content is correct
- Local installation works
- Global installation works
- Files install to correct locations

This is the final quality check before publishing.

---

## Steps

### 1. Run Package Validation

Execute the validation command:
```bash
@acp.package-validate
```

**Expected Checks**:
- package.yaml schema validation
- All referenced files exist
- Namespace consistency
- No duplicate names
- README.md auto-update markers present

**Fix any errors** before proceeding.

### 2. Test Local Installation

Test installing package to a local project:

```bash
# Create test project
mkdir /tmp/test-local-install
cd /tmp/test-local-install

# Initialize ACP
curl -fsSL https://raw.githubusercontent.com/prmichaelsen/agent-context-protocol/mainline/agent/scripts/acp.install.sh | bash

# Install package locally
@acp.package-install /path/to/acp-mcp-server-starter
```

**Verify**:
- [ ] All patterns installed to `agent/patterns/`
- [ ] All commands installed to `agent/commands/`
- [ ] All designs installed to `agent/design/`
- [ ] manifest.yaml updated with package info
- [ ] Files have correct namespace prefix

### 3. Test Global Installation

Test installing package globally:

```bash
# Install globally
@acp.package-install --global /path/to/acp-mcp-server-starter

# Verify global installation
ls ~/.acp/agent/patterns/ | grep mcp-server-starter
ls ~/.acp/agent/commands/ | grep mcp-server-starter
ls ~/.acp/agent/design/ | grep mcp-server-starter
cat ~/.acp/agent/manifest.yaml
```

**Verify**:
- [ ] Files installed to `~/.acp/agent/`
- [ ] Global manifest.yaml updated
- [ ] Commands discoverable globally

### 4. Test Command Discovery

Test that commands are discoverable:

```bash
# In any project with ACP
@mcp-server-starter.init-project --help
@mcp-server-starter.add-tool --help
```

**Verify**:
- [ ] Commands are found
- [ ] Help text displays correctly

### 5. Test Pattern Access

Verify patterns are readable:

```bash
# Read a pattern
cat agent/patterns/mcp-server-starter.bootstrap.md
```

**Verify**:
- [ ] Patterns are well-formatted
- [ ] Code examples are complete
- [ ] Cross-references work

### 6. Review README.md

Check that README.md auto-updated correctly:

**Verify**:
- [ ] Pattern list is complete
- [ ] Command list is complete
- [ ] Design list is complete
- [ ] Descriptions are accurate

### 7. Clean Up Test Installations

Remove test directories:
```bash
rm -rf /tmp/test-local-install
```

---

## Verification

- [ ] `@acp.package-validate` passes with no errors
- [ ] Local installation tested successfully
- [ ] Global installation tested successfully
- [ ] All files install to correct locations
- [ ] Commands are discoverable
- [ ] Patterns are readable
- [ ] README.md is correct
- [ ] No broken links or references

---

## Deliverables

### Validation Report
- Document any issues found
- Confirm all tests passed
- List any fixes applied

---

## Notes

- Fix all validation errors before publishing
- Test both local and global installation
- Verify namespace consistency
- Check that all cross-references work

---

**Previous Task**: [Task 13: Build Example Starter Template](task-13-build-example-template.md)
**Next Task**: [Task 15: Publish Package to Repository](task-15-publish-package.md)
