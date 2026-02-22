# Task 15: Publish Package to Repository

**Milestone**: M3 - Package Validation & Publishing
**Estimated Time**: 1-2 hours
**Dependencies**: Task 14 (Validation and Testing)
**Status**: Not Started

---

## Objective

Publish the validated package to the git repository with proper versioning, changelog updates, and git tags for distribution.

---

## Context

Publishing involves:
- Updating CHANGELOG.md with release notes
- Creating git tag for version
- Pushing to repository
- Testing remote installation
- Announcing release

This makes the package available for users to install.

---

## Steps

### 1. Review Package Version

Check current version in [`package.yaml`](../../../package.yaml:1):
```yaml
version: 1.0.0
```

Confirm this is the correct version for release.

### 2. Update CHANGELOG.md

Add release notes to [`CHANGELOG.md`](../../../CHANGELOG.md:1):

```markdown
## [1.0.0] - 2026-02-22

### Added
- 7 pattern documents for MCP server development
  - Bootstrap pattern (project initialization)
  - Server standalone pattern (stdio transport)
  - Server factory pattern (mcp-auth integration)
  - Tool creation pattern (MCP tools)
  - Build config pattern (esbuild setup)
  - Test config pattern (Jest + TypeScript)
  - Config management pattern (environment variables)
- 2 command documents
  - init-project command (scaffold new projects)
  - add-tool command (generate tool scaffolding)
- 2 design documents
  - Architecture design (dual export pattern)
  - mcp-auth integration design (multi-tenancy)
- Complete analysis of remember-mcp patterns
- Comprehensive documentation for TypeScript MCP servers

### Changed
- Initial release

### Fixed
- N/A (initial release)
```

### 3. Commit Changes

Commit all changes:
```bash
git add .
git commit -m "chore: release v1.0.0

- Add 7 patterns for MCP server development
- Add 2 commands for project scaffolding
- Add 2 design documents for architecture
- Complete package documentation"
```

### 4. Create Git Tag

Create annotated tag:
```bash
git tag -a v1.0.0 -m "Release v1.0.0

First release of mcp-server-starter package with complete
pattern documentation for building TypeScript MCP servers."
```

### 5. Push to Repository

Push commits and tags:
```bash
git push origin main
git push origin v1.0.0
```

### 6. Test Remote Installation

Test installing from remote repository:

```bash
# Create test project
mkdir /tmp/test-remote-install
cd /tmp/test-remote-install

# Initialize ACP
curl -fsSL https://raw.githubusercontent.com/prmichaelsen/agent-context-protocol/mainline/agent/scripts/acp.install.sh | bash

# Install package from remote
@acp.package-install https://github.com/prmichaelsen/acp-mcp-server-starter.git
```

**Verify**:
- [ ] Package installs successfully
- [ ] All files present
- [ ] Commands work
- [ ] Patterns readable

### 7. Update Package Status

Update [`agent/progress.yaml`](../../progress.yaml:1):
- Set project status to `completed`
- Update overall progress to 100%
- Add final recent_work entry

### 8. Create Release Notes (Optional)

If using GitHub releases, create release:
- Go to repository releases
- Create new release from v1.0.0 tag
- Copy CHANGELOG.md content
- Publish release

---

## Verification

- [ ] CHANGELOG.md updated with release notes
- [ ] Git commit created
- [ ] Git tag created (v1.0.0)
- [ ] Changes pushed to repository
- [ ] Tag pushed to repository
- [ ] Remote installation tested successfully
- [ ] progress.yaml updated
- [ ] GitHub release created (optional)

---

## Deliverables

### Files Modified
- `CHANGELOG.md` (release notes)
- `agent/progress.yaml` (final status)

### Git Artifacts
- Commit with release changes
- Tag v1.0.0
- GitHub release (optional)

---

## Notes

- Ensure all validation passed before publishing
- Test remote installation before announcing
- Follow semantic versioning for future releases
- Consider creating GitHub release for visibility

---

**Previous Task**: [Task 14: Validate Package and Test Installation](task-14-validate-and-test.md)
**Next Task**: None (Package Complete!)
