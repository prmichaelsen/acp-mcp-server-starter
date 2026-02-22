# Task 10: Create add-tool Command

**Milestone**: M2 - Command & Design Documentation
**Estimated Time**: 2-3 hours
**Dependencies**: Task 9 (init-project Command)
**Status**: Not Started

---

## Objective

Create the add-tool command document that provides a workflow for generating new tool scaffolding in an existing MCP server project.

---

## Context

The add-tool command automates tool creation by:
- Generating tool file from template
- Creating TypeScript interfaces
- Adding tool to server registration
- Creating test file
- Updating documentation

This command speeds up tool development and ensures consistency.

---

## Steps

### 1. Review Tool Creation Pattern

Read [`mcp-server-starter.tool-creation`](../../patterns/mcp-server-starter.tool-creation.md) pattern (if exists).

### 2. Create Command Document

Create `agent/commands/mcp-server-starter.add-tool.md` using the command template.

**Sections to Include**:
- **Purpose**: Generate new tool scaffolding
- **Prerequisites**: Existing MCP server project
- **Steps**: Complete workflow
- **Verification**: Checklist
- **Expected Output**: Files created
- **Examples**: Usage scenarios
- **Troubleshooting**: Common issues

### 3. Define Command Steps

Document the workflow:

1. **Gather Tool Information**
   - Tool name (e.g., "search_documents")
   - Description
   - Parameters (name, type, description, required)

2. **Generate Tool File**
   - Create `src/tools/{tool-name}.ts`
   - Tool definition object
   - TypeScript interfaces
   - Handler function

3. **Update Server Registration**
   - Add tool to ListToolsRequestSchema handler
   - Add case to CallToolRequestSchema handler

4. **Create Test File**
   - Create `src/tools/{tool-name}.spec.ts`
   - Basic test cases

5. **Provide Next Steps**
   - Implement tool logic
   - Add more tests
   - Update documentation

### 4. Add Tool Template

Include complete tool template:
```typescript
export const {toolName}Tool = {
  name: '{tool_name}',
  description: '{description}',
  inputSchema: {
    type: 'object',
    properties: {
      // parameters
    },
    required: [],
  },
};

export interface {ToolName}Args {
  // args interface
}

export interface {ToolName}Result {
  // result interface
}

export async function handle{ToolName}(
  args: {ToolName}Args,
  userId: string
): Promise<string> {
  try {
    // TODO: Implement tool logic
    
    const result: {ToolName}Result = {
      // result
    };
    
    return JSON.stringify(result, null, 2);
  } catch (error) {
    handleToolError(error, {
      toolName: '{tool_name}',
      operation: '{operation}',
      userId,
    });
  }
}
```

### 5. Document Command Invocation

Show usage:
```bash
@mcp-server-starter.add-tool
```

Or with arguments:
```bash
@mcp-server-starter.add-tool --name search_documents --description "Search documents by query"
```

### 6. Update package.yaml

Add command to contents.commands array.

---

## Verification

- [ ] Command document created
- [ ] All steps documented
- [ ] Tool template included
- [ ] Server update steps shown
- [ ] Test file generation covered
- [ ] package.yaml updated
- [ ] README.md auto-updated

---

## Deliverables

### Files Created
- `agent/commands/mcp-server-starter.add-tool.md`

### Files Modified
- `package.yaml`
- `README.md` (auto-updated)

---

**Previous Task**: [Task 9: Create init-project Command](task-9-init-project-command.md)
**Next Task**: [Task 11: Create Architecture Design Document](task-11-architecture-design.md)
