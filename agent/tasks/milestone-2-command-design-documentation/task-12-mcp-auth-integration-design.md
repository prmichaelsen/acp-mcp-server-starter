# Task 12: Create mcp-auth Integration Design Document

**Milestone**: M2 - Command & Design Documentation
**Estimated Time**: 2-3 hours
**Dependencies**: Task 11 (Architecture Design)
**Status**: Not Started

---

## Objective

Create the mcp-auth integration design document that explains how to integrate MCP servers with mcp-auth for multi-tenant production deployments.

---

## Context

The mcp-auth integration design explains:
- What is mcp-auth and why use it
- How the factory pattern enables multi-tenancy
- Authentication flow
- User isolation strategy
- Production deployment patterns

This helps developers understand when and how to use mcp-auth.

---

## Steps

### 1. Review Analysis Document

Read the "Pattern 2: Server Factory (mcp-auth Integration)" section in [`agent/design/remember-mcp-analysis.md`](../../design/remember-mcp-analysis.md).

### 2. Create Design Document

Create `agent/design/mcp-server-starter.mcp-auth-integration.md` using the design template.

**Sections to Include**:
- **Concept**: One-line mcp-auth description
- **Overview**: What is mcp-auth
- **Problem Statement**: Why multi-tenancy is needed
- **Solution**: How factory pattern enables it
- **Authentication Flow**: Step-by-step flow
- **User Isolation**: How userId scopes operations
- **Implementation**: Complete integration example
- **Benefits**: Advantages of mcp-auth
- **Trade-offs**: When NOT to use mcp-auth

### 3. Add Authentication Flow Diagram

Create ASCII diagram:
```
┌─────────┐      ┌──────────┐      ┌─────────────┐
│ Client  │─────▶│ mcp-auth │─────▶│ MCP Server  │
│         │      │ Wrapper  │      │  Factory    │
└─────────┘      └──────────┘      └─────────────┘
     │                │                    │
     │ 1. Request     │                    │
     │    + JWT       │                    │
     │                │                    │
     │           2. Validate JWT           │
     │           3. Extract userId         │
     │                │                    │
     │                │  4. createServer(  │
     │                │     accessToken,   │
     │                │     userId,        │
     │                │     options)       │
     │                │                    │
     │                │         5. Return  │
     │                │            isolated│
     │                │            server  │
     │                │                    │
     │           6. Route request          │
     │              to server              │
     │                │                    │
     │◀───────────────┴────────────────────┘
     │           7. Response
```

### 4. Document Factory Function Contract

Explain the createServer signature:
```typescript
export async function createServer(
  accessToken: string,  // For external APIs (optional)
  userId: string,       // For user scoping (required)
  options?: ServerOptions
): Promise<Server>
```

### 5. Add Complete Integration Example

Show full mcp-auth setup:
```typescript
import { wrapServer, JWTAuthProvider } from '@prmichaelsen/mcp-auth';
import { createServer } from './server-factory.js';

const wrapped = wrapServer({
  serverFactory: createServer,
  authProvider: new JWTAuthProvider({
    jwtSecret: process.env.JWT_SECRET
  }),
  resourceType: 'my-resource',
  transport: { type: 'sse', port: 3000 }
});

await wrapped.start();
```

### 6. Document User Isolation Strategy

Explain how userId flows through the system:
- Factory receives userId
- Handlers receive userId
- Tools use userId for scoping
- No shared state between users

### 7. Add Decision Records

Document when to use mcp-auth:
- ✅ Production multi-tenant deployments
- ✅ User authentication required
- ✅ SSE or HTTP transport
- ❌ Claude Desktop (use standalone)
- ❌ Single-user deployments
- ❌ Stdio transport

### 8. Update package.yaml

Add design to contents.designs array.

---

## Verification

- [ ] Design document created
- [ ] Authentication flow diagram included
- [ ] Factory contract explained
- [ ] Integration example complete
- [ ] User isolation documented
- [ ] Decision records added
- [ ] package.yaml updated
- [ ] README.md auto-updated

---

## Deliverables

### Files Created
- `agent/design/mcp-server-starter.mcp-auth-integration.md`

### Files Modified
- `package.yaml`
- `README.md` (auto-updated)

---

**Previous Task**: [Task 11: Create Architecture Design Document](task-11-architecture-design.md)
**Next Task**: [Task 13: Build Example Starter Template](../../milestone-3-package-validation-publishing/task-13-build-example-template.md) (Milestone 3)
