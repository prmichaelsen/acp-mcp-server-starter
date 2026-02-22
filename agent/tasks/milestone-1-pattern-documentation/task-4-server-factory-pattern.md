# Task 4: Create Server Factory Pattern

**Milestone**: M1 - Pattern Documentation
**Estimated Time**: 3-4 hours
**Dependencies**: Task 3 (Server Standalone Pattern)
**Status**: Not Started

---

## Objective

Create the server factory pattern document that shows developers how to build multi-tenant MCP servers compatible with mcp-auth for production deployments.

---

## Context

The factory pattern enables:
- Multi-tenant architecture with per-user isolation
- mcp-auth compatibility
- Global database initialization (once per process)
- Per-user server instances (no shared state)
- Production-ready scalability

This pattern is essential for production MCP servers that serve multiple users.

---

## Steps

### 1. Review Analysis Document

Read "Pattern 2: Server Factory (mcp-auth Integration)" in [`agent/design/remember-mcp-analysis.md`](../../design/remember-mcp-analysis.md).

### 2. Create Pattern Document

Create `agent/patterns/mcp-server-starter.server-factory.md`.

**Sections to Include**:
- **Overview**: Factory pattern for multi-tenancy
- **Core Principles**: User isolation, global init, no shared state
- **Implementation**: Complete server-factory.ts walkthrough
- **Global Initialization**: Database setup pattern
- **Factory Function**: createServer signature
- **User Scoping**: How userId flows through handlers
- **mcp-auth Integration**: Usage with wrapServer
- **Examples**: Complete factory + mcp-auth usage
- **Benefits**: Scalability and isolation
- **Anti-Patterns**: Shared state mistakes

### 3. Add Complete Code Example

Include complete `server-factory.ts` with:
- Global initialization pattern
- ensureDatabasesInitialized() function
- createServer(accessToken, userId, options) signature
- Handler registration with userId scoping
- ServerOptions interface

### 4. Document mcp-auth Integration

Show how to use the factory with mcp-auth:
```typescript
import { wrapServer } from '@prmichaelsen/mcp-auth';
import { createServer } from './server-factory.js';

const wrapped = wrapServer({
  serverFactory: createServer,
  authProvider: new JWTAuthProvider({ ... }),
  resourceType: 'resource-name',
  transport: { type: 'sse', port: 3000 }
});
```

### 5. Explain Dual Export Pattern

Document how to export both standalone and factory:
```json
{
  "exports": {
    ".": "./dist/server.js",
    "./factory": "./dist/server-factory.js"
  }
}
```

### 6. Update package.yaml

Add pattern to contents.patterns array.

---

## Verification

- [ ] Pattern document created
- [ ] Complete server-factory.ts example included
- [ ] Global initialization pattern documented
- [ ] mcp-auth integration shown
- [ ] Dual export pattern explained
- [ ] package.yaml updated
- [ ] README.md auto-updated

---

## Deliverables

### Files Created
- `agent/patterns/mcp-server-starter.server-factory.md`

### Files Modified
- `package.yaml`
- `README.md` (auto-updated)

---

**Previous Task**: [Task 3: Create Server Standalone Pattern](task-3-server-standalone-pattern.md)
**Next Task**: [Task 5: Create Tool Creation Pattern](task-5-tool-creation-pattern.md)
