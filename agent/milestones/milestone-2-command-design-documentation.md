# Milestone 2: Command & Design Documentation

**Goal**: Create command workflows and architectural design documents
**Duration**: 1-2 weeks
**Dependencies**: Milestone 1 (Pattern Documentation)
**Status**: Not Started

---

## Overview

This milestone creates the command workflows that users will invoke to scaffold new MCP server projects and add tools. It also documents the overall architecture and mcp-auth integration patterns through design documents.

Commands provide automated workflows for common tasks, while design documents explain the "why" behind architectural decisions.

---

## Deliverables

1. **2 Command Documents** in `agent/commands/`:
   - `mcp-server-starter.init-project.md` - Initialize new MCP server project
   - `mcp-server-starter.add-tool.md` - Generate new tool scaffolding

2. **2 Design Documents** in `agent/design/`:
   - `mcp-server-starter.architecture.md` - Overall architecture and dual export pattern
   - `mcp-server-starter.mcp-auth-integration.md` - Multi-tenancy and authentication

3. **Updated package.yaml** with command and design references

4. **Updated README.md** with command and design listings

---

## Success Criteria

- [ ] Both command documents created with complete workflows
- [ ] Each command includes:
  - [ ] Purpose and description
  - [ ] Prerequisites
  - [ ] Step-by-step instructions
  - [ ] Verification checklist
  - [ ] Examples and troubleshooting
- [ ] Both design documents created with architectural guidance
- [ ] Each design includes:
  - [ ] Problem statement
  - [ ] Solution approach
  - [ ] Implementation details
  - [ ] Benefits and trade-offs
- [ ] package.yaml contents section updated
- [ ] README.md auto-updated with command and design lists
- [ ] All documents validated with `@acp.package-validate`

---

## Key Files to Create

```
agent/commands/
├── mcp-server-starter.init-project.md
└── mcp-server-starter.add-tool.md

agent/design/
├── mcp-server-starter.architecture.md
└── mcp-server-starter.mcp-auth-integration.md
```

---

## Tasks

- [Task 9](../tasks/milestone-2-command-design-documentation/task-9-init-project-command.md): Create init-project Command
- [Task 10](../tasks/milestone-2-command-design-documentation/task-10-add-tool-command.md): Create add-tool Command
- [Task 11](../tasks/milestone-2-command-design-documentation/task-11-architecture-design.md): Create Architecture Design Document
- [Task 12](../tasks/milestone-2-command-design-documentation/task-12-mcp-auth-integration-design.md): Create mcp-auth Integration Design Document

---

**Previous Milestone**: [Milestone 1: Pattern Documentation](milestone-1-pattern-documentation.md)
**Next Milestone**: [Milestone 3: Package Validation & Publishing](milestone-3-package-validation-publishing.md)
**Blockers**: None
