# Task 2: Create Bootstrap Pattern

**Milestone**: M1 - Pattern Documentation
**Estimated Time**: 2-3 hours
**Dependencies**: Task 1 (Analysis) - Completed
**Status**: Not Started

---

## Objective

Create the bootstrap pattern document that guides developers through initializing a new MCP server project with the correct directory structure, configuration files, and dependencies.

---

## Context

From the remember-mcp analysis, we identified that project initialization follows a specific pattern:
- Standard directory structure (src/, dist/, tests/)
- Configuration files (package.json, tsconfig.json, esbuild, jest)
- Environment setup (.env.example)
- Git initialization
- npm scripts for dev/build/test

This pattern should be extracted into a reusable document that explains the "why" and "how" of each component.

---

## Steps

### 1. Review Analysis Document

Read the Bootstrap Pattern section in [`agent/design/remember-mcp-analysis.md`](../../design/remember-mcp-analysis.md).

**Key Points to Extract**:
- Directory structure rationale
- Essential configuration files
- Dependency choices
- Development workflow setup

### 2. Create Pattern Document

Create `agent/patterns/mcp-server-starter.bootstrap.md` using the pattern template.

**Sections to Include**:
- **Overview**: What is the bootstrap pattern and when to use it
- **Core Principles**: Key concepts (ESM, TypeScript, dual build)
- **Directory Structure**: Explain each directory's purpose
- **Configuration Files**: Detail each config file
- **Dependencies**: Core vs dev dependencies with rationale
- **Implementation**: Step-by-step setup guide
- **Examples**: Code snippets for each config file
- **Benefits**: Why this structure works well
- **Anti-Patterns**: Common mistakes to avoid

### 3. Add Code Examples

Include complete, working examples for:
- `package.json` with scripts and dependencies
- `tsconfig.json` with ES2022 + ESM settings
- `.env.example` template
- `.gitignore` for MCP projects
- Basic `README.md` structure

### 4. Cross-Reference Other Patterns

Link to related patterns:
- Server Standalone Pattern (uses this structure)
- Server Factory Pattern (uses this structure)
- Build Config Pattern (builds on this structure)

### 5. Update package.yaml

Add pattern to `contents.patterns` array in [`package.yaml`](../../../package.yaml:1):
```yaml
contents:
  patterns:
    - name: bootstrap
      file: mcp-server-starter.bootstrap.md
      description: Project initialization and directory structure
```

### 6. Verify Auto-Update

Confirm that README.md auto-updates with the new pattern (should happen automatically via package tooling).

---

## Verification

- [ ] Pattern document created at `agent/patterns/mcp-server-starter.bootstrap.md`
- [ ] All sections complete with detailed explanations
- [ ] Code examples are complete and accurate
- [ ] Cross-references to other patterns included
- [ ] package.yaml updated with pattern entry
- [ ] README.md shows new pattern in list
- [ ] Pattern follows template structure
- [ ] No typos or formatting issues

---

## Deliverables

### Files Created
- `agent/patterns/mcp-server-starter.bootstrap.md`

### Files Modified
- `package.yaml` (contents.patterns array)
- `README.md` (auto-updated)

---

## Notes

- Use remember-mcp as the reference implementation
- Focus on the "why" not just the "what"
- Include anti-patterns to help developers avoid mistakes
- Keep examples minimal but complete
- Ensure all code examples use ESM syntax (import/export)

---

**Next Task**: [Task 3: Create Server Standalone Pattern](task-3-server-standalone-pattern.md)
