# Task 11: Create Architecture Design Document

**Milestone**: M2 - Command & Design Documentation
**Estimated Time**: 2-3 hours
**Dependencies**: Milestone 1 (All patterns completed)
**Status**: Not Started

---

## Objective

Create the architecture design document that explains the overall MCP server architecture, dual export pattern, and component relationships.

---

## Context

The architecture design document provides the "big picture" view:
- Why dual export (standalone + factory)
- How components fit together
- When to use each pattern
- Design decisions and rationale

This helps developers understand the overall system design.

---

## Steps

### 1. Review Analysis Document

Read the "Architecture Summary" section in [`agent/design/remember-mcp-analysis.md`](../../design/remember-mcp-analysis.md).

### 2. Create Design Document

Create `agent/design/mcp-server-starter.architecture.md` using the design template.

**Sections to Include**:
- **Concept**: One-line architecture description
- **Overview**: High-level architecture explanation
- **Problem Statement**: Why this architecture
- **Solution**: How dual export solves the problem
- **Components**: Server, factory, tools, config
- **Component Relationships**: How they interact
- **Dual Export Pattern**: Detailed explanation
- **Implementation**: Technical details
- **Benefits**: Advantages of this architecture
- **Trade-offs**: Limitations and considerations

### 3. Add Architecture Diagram

Create ASCII diagram showing:
```
┌─────────────────────────────────────────┐
│         MCP Server Package              │
├─────────────────────────────────────────┤
│                                         │
│  ┌──────────────┐  ┌─────────────────┐ │
│  │   server.ts  │  │ server-factory  │ │
│  │  (Standalone)│  │   .ts (Multi-   │ │
│  │              │  │    tenant)      │ │
│  └──────┬───────┘  └────────┬────────┘ │
│         │                   │          │
│         └───────┬───────────┘          │
│                 │                      │
│         ┌───────▼────────┐             │
│         │  Tools Layer   │             │
│         │  - Tool defs   │             │
│         │  - Handlers    │             │
│         └───────┬────────┘             │
│                 │                      │
│         ┌───────▼────────┐             │
│         │  Config Layer  │             │
│         │  - Validation  │             │
│         │  - Env vars    │             │
│         └────────────────┘             │
│                                         │
└─────────────────────────────────────────┘
```

### 4. Explain Dual Export Pattern

Document the pattern in detail:
- **Standalone**: For Claude Desktop, direct execution
- **Factory**: For mcp-auth, production multi-tenancy
- **Shared Code**: Tools, config, utilities
- **package.json exports**: How to configure

### 5. Document Component Responsibilities

Explain each component:
- **Server**: Request handling, tool routing
- **Factory**: User isolation, global init
- **Tools**: Business logic, MCP tool interface
- **Config**: Environment, validation
- **Utils**: Error handling, logging

### 6. Add Decision Records

Document key architectural decisions:
- Why ESM over CommonJS
- Why esbuild over webpack
- Why dual build over single build
- Why stdio for standalone

### 7. Update package.yaml

Add design to contents.designs array:
```yaml
contents:
  designs:
    - name: architecture
      file: mcp-server-starter.architecture.md
      description: Overall architecture and dual export pattern
```

---

## Verification

- [ ] Design document created
- [ ] Architecture diagram included
- [ ] Dual export pattern explained
- [ ] Component responsibilities documented
- [ ] Design decisions recorded
- [ ] package.yaml updated
- [ ] README.md auto-updated

---

## Deliverables

### Files Created
- `agent/design/mcp-server-starter.architecture.md`

### Files Modified
- `package.yaml`
- `README.md` (auto-updated)

---

**Previous Task**: [Task 10: Create add-tool Command](task-10-add-tool-command.md)
**Next Task**: [Task 12: Create mcp-auth Integration Design Document](task-12-mcp-auth-integration-design.md)
