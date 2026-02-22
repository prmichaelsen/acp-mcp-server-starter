# Task 8: Create Config Management Pattern

**Milestone**: M1 - Pattern Documentation
**Estimated Time**: 2-3 hours
**Dependencies**: Task 2 (Bootstrap Pattern)
**Status**: Not Started

---

## Objective

Create the configuration management pattern document that shows developers how to handle environment variables, validation, and type-safe configuration access.

---

## Context

MCP servers need robust configuration management:
- Environment variables with dotenv
- Type-safe config object
- Validation function
- Default values
- .env.example template

This pattern ensures configuration is reliable and maintainable.

---

## Steps

### 1. Review Analysis Document

Read "Pattern 7: Configuration Management" in [`agent/design/remember-mcp-analysis.md`](../../design/remember-mcp-analysis.md).

### 2. Create Pattern Document

Create `agent/patterns/mcp-server-starter.config-management.md`.

**Sections to Include**:
- **Overview**: Configuration management for MCP servers
- **Core Principles**: Type safety, validation, defaults
- **dotenv Setup**: Loading environment variables
- **Config Object**: Type-safe configuration structure
- **Validation**: Required vs optional config
- **Default Values**: Sensible defaults
- **.env.example**: Template for users
- **Examples**: Complete config.ts
- **Benefits**: Reliability and maintainability
- **Anti-Patterns**: Common config mistakes

### 3. Add Complete config.ts Example

Include complete configuration with:
- dotenv.config() call
- Typed config object (as const)
- Service configurations
- Server settings
- validateConfig() function

### 4. Add .env.example Template

Show complete .env.example:
```bash
# Service Configuration
SERVICE_URL=http://localhost:8080
SERVICE_API_KEY=

# Server Configuration
PORT=3000
NODE_ENV=development
LOG_LEVEL=info
```

### 5. Document Validation Pattern

Show validation function:
```typescript
export function validateConfig(): void {
  const required = [
    { key: 'SERVICE_URL', value: config.service.url },
    { key: 'SERVICE_API_KEY', value: config.service.apiKey },
  ];
  
  const missing = required.filter((r) => !r.value);
  
  if (missing.length > 0) {
    throw new Error(
      `Missing required environment variables: ${missing.map((m) => m.key).join(', ')}`
    );
  }
}
```

### 6. Document Usage in Server

Show how config is used:
```typescript
import { config, validateConfig } from './config.js';

async function initServer() {
  validateConfig();
  // ... use config.service.url, etc.
}
```

### 7. Update package.yaml

Add pattern to contents.patterns array.

---

## Verification

- [ ] Pattern document created
- [ ] Complete config.ts example included
- [ ] Validation pattern documented
- [ ] .env.example template provided
- [ ] Usage examples shown
- [ ] package.yaml updated
- [ ] README.md auto-updated

---

## Deliverables

### Files Created
- `agent/patterns/mcp-server-starter.config-management.md`

### Files Modified
- `package.yaml`
- `README.md` (auto-updated)

---

**Previous Task**: [Task 7: Create Test Config Pattern](task-7-test-config-pattern.md)
**Next Task**: [Task 9: Create init-project Command](../../milestone-2-command-design-documentation/task-9-init-project-command.md) (Milestone 2)
