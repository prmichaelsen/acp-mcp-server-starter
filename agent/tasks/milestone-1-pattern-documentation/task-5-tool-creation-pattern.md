# Task 5: Create Tool Creation Pattern

**Milestone**: M1 - Pattern Documentation
**Estimated Time**: 3-4 hours
**Dependencies**: Task 3 (Server Standalone Pattern)
**Status**: Not Started

---

## Objective

Create the tool creation pattern document that shows developers how to build MCP tools with proper structure, type safety, and error handling.

---

## Context

MCP tools are the core functionality of an MCP server. The tool creation pattern covers:
- Tool definition object (name, description, inputSchema)
- TypeScript interfaces for args and results
- Handler function signature
- Input validation
- Error handling
- Response formatting (JSON strings)

This pattern ensures consistent, type-safe tool implementation.

---

## Steps

### 1. Review Analysis Document

Read "Pattern 3: Tool Creation" in [`agent/design/remember-mcp-analysis.md`](../../design/remember-mcp-analysis.md).

### 2. Create Pattern Document

Create `agent/patterns/mcp-server-starter.tool-creation.md`.

**Sections to Include**:
- **Overview**: What are MCP tools and how to create them
- **Core Principles**: Schema-first, type-safe, JSON responses
- **Tool Definition**: Schema object structure
- **TypeScript Interfaces**: Args and Result types
- **Handler Function**: Signature and implementation
- **Input Validation**: Parameter checking
- **Error Handling**: McpError and handleToolError
- **Response Formatting**: JSON.stringify pattern
- **File Organization**: One tool per file
- **Examples**: Complete hello_computer tool
- **Benefits**: Type safety and consistency
- **Anti-Patterns**: Common mistakes

### 3. Add Complete hello_computer Example

Include the minimal example tool:
```typescript
export const helloComputerTool = {
  name: 'hello_computer',
  description: 'Returns a friendly greeting',
  inputSchema: {
    type: 'object',
    properties: {
      name: {
        type: 'string',
        description: 'Optional name to greet',
      },
    },
    required: [],
  },
};

export interface HelloComputerArgs {
  name?: string;
}

export interface HelloComputerResult {
  message: string;
  timestamp: string;
}

export async function handleHelloComputer(
  args: HelloComputerArgs,
  userId: string
): Promise<string> {
  const greeting = args.name 
    ? `Hello, ${args.name}!` 
    : 'Hello, world!';
  
  const result: HelloComputerResult = {
    message: greeting,
    timestamp: new Date().toISOString(),
  };
  
  return JSON.stringify(result, null, 2);
}
```

### 4. Document Tool Registration

Show how tools are registered in server:
```typescript
server.setRequestHandler(ListToolsRequestSchema, async () => {
  return {
    tools: [
      helloComputerTool,
      // ... other tools
    ],
  };
});
```

### 5. Document Tool Execution

Show handler routing pattern:
```typescript
server.setRequestHandler(CallToolRequestSchema, async (request) => {
  const { name, arguments: args } = request.params;
  
  switch (name) {
    case 'hello_computer':
      result = await handleHelloComputer(args as any, userId);
      break;
    // ... other tools
  }
  
  return {
    content: [{ type: 'text', text: result }],
  };
});
```

### 6. Update package.yaml

Add pattern to contents.patterns array.

---

## Verification

- [ ] Pattern document created
- [ ] Complete hello_computer example included
- [ ] Tool definition schema documented
- [ ] Handler function pattern shown
- [ ] Registration and routing explained
- [ ] Error handling covered
- [ ] package.yaml updated
- [ ] README.md auto-updated

---

## Deliverables

### Files Created
- `agent/patterns/mcp-server-starter.tool-creation.md`

### Files Modified
- `package.yaml`
- `README.md` (auto-updated)

---

**Previous Task**: [Task 4: Create Server Factory Pattern](task-4-server-factory-pattern.md)
**Next Task**: [Task 6: Create Build Config Pattern](task-6-build-config-pattern.md)
