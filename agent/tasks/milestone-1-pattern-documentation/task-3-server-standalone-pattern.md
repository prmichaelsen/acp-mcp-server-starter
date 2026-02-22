# Task 3: Create Server Standalone Pattern

**Milestone**: M1 - Pattern Documentation
**Estimated Time**: 3-4 hours
**Dependencies**: Task 2 (Bootstrap Pattern)
**Status**: Not Started

---

## Objective

Create the server standalone pattern document that shows developers how to build a basic MCP server with stdio transport for use with Claude Desktop or standalone execution.

---

## Context

The standalone server pattern is the simplest MCP server architecture:
- Single entry point (`src/server.ts`)
- Stdio transport for JSON-RPC communication
- Tool registration and handler routing
- Error handling with McpError types
- Graceful shutdown

This is the foundation pattern that all MCP servers build upon.

---

## Steps

### 1. Review Analysis Document

Read the "Pattern 1: MCP Server Setup (Standalone)" section in [`agent/design/remember-mcp-analysis.md`](../../design/remember-mcp-analysis.md).

### 2. Create Pattern Document

Create `agent/patterns/mcp-server-starter.server-standalone.md`.

**Sections to Include**:
- **Overview**: Standalone server architecture
- **Core Principles**: Stdio transport, handler registration, error handling
- **Implementation**: Complete server.ts walkthrough
- **Tool Registration**: How to register tools
- **Handler Routing**: Switch statement pattern
- **Error Handling**: McpError usage
- **Graceful Shutdown**: Signal handlers
- **Examples**: Complete working server
- **Benefits**: When to use standalone vs factory
- **Anti-Patterns**: Common mistakes

### 3. Add Complete Code Example

Include a minimal but complete `server.ts` with:
- Imports from @modelcontextprotocol/sdk
- Server initialization
- Tool registration (ListToolsRequestSchema)
- Tool execution (CallToolRequestSchema)
- Error handling
- Main function with stdio transport
- Shutdown handlers

### 4. Document Tool Handler Pattern

Show the standard pattern for tool handlers:
```typescript
case 'tool_name':
  result = await handleTool(args as any, userId);
  break;
```

### 5. Update package.yaml

Add pattern to contents.patterns array.

---

## Verification

- [ ] Pattern document created
- [ ] Complete server.ts example included
- [ ] Tool registration pattern documented
- [ ] Error handling explained
- [ ] Graceful shutdown covered
- [ ] package.yaml updated
- [ ] README.md auto-updated

---

## Deliverables

### Files Created
- `agent/patterns/mcp-server-starter.server-standalone.md`

### Files Modified
- `package.yaml`
- `README.md` (auto-updated)

---

**Previous Task**: [Task 2: Create Bootstrap Pattern](task-2-bootstrap-pattern.md)
**Next Task**: [Task 4: Create Server Factory Pattern](task-4-server-factory-pattern.md)
