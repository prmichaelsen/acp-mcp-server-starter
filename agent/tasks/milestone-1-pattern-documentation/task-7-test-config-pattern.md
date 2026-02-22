# Task 7: Create Test Config Pattern

**Milestone**: M1 - Pattern Documentation
**Estimated Time**: 2-3 hours
**Dependencies**: Task 2 (Bootstrap Pattern)
**Status**: Not Started

---

## Objective

Create the test configuration pattern document that shows developers how to set up Jest with TypeScript and ESM for testing MCP servers.

---

## Context

Testing MCP servers requires special configuration:
- Jest with ts-jest for TypeScript
- ESM support (not CommonJS)
- Path alias mapping (@/ → src/)
- Colocated tests (*.spec.ts)
- Coverage configuration

This pattern ensures reliable testing for MCP server projects.

---

## Steps

### 1. Review Analysis Document

Read "Pattern 6: Testing Configuration (Jest)" in [`agent/design/remember-mcp-analysis.md`](../../design/remember-mcp-analysis.md).

### 2. Create Pattern Document

Create `agent/patterns/mcp-server-starter.test-config.md`.

**Sections to Include**:
- **Overview**: Testing MCP servers with Jest
- **Core Principles**: ESM, TypeScript, colocated tests
- **Jest Configuration**: Complete config walkthrough
- **ESM Support**: ts-jest preset and settings
- **Path Aliases**: Module name mapping
- **Test Organization**: Colocated vs separate
- **Coverage**: Configuration and thresholds
- **Examples**: Complete jest.config.js
- **Benefits**: Reliable testing
- **Anti-Patterns**: Common test config mistakes

### 3. Add Complete jest.config.js Example

Include complete config with:
- ESM preset
- TypeScript transform
- Path alias mapping
- Coverage settings
- Test match patterns

### 4. Document Test Organization

Show two approaches:
- **Colocated**: `src/**/*.spec.ts` (recommended)
- **Separate**: `tests/**/*.test.ts`

### 5. Add Example Test

Include a simple test example:
```typescript
import { describe, it, expect } from '@jest/globals';
import { handleHelloComputer } from './hello-computer.js';

describe('hello_computer tool', () => {
  it('should return greeting', async () => {
    const result = await handleHelloComputer({}, 'user123');
    const parsed = JSON.parse(result);
    expect(parsed.message).toBe('Hello, world!');
  });
});
```

### 6. Document npm Scripts

Show test scripts:
```json
{
  "scripts": {
    "test": "jest",
    "test:watch": "jest --watch",
    "test:coverage": "jest --coverage"
  }
}
```

### 7. Update package.yaml

Add pattern to contents.patterns array.

---

## Verification

- [ ] Pattern document created
- [ ] Complete jest.config.js example included
- [ ] ESM configuration explained
- [ ] Test organization documented
- [ ] Example test provided
- [ ] npm scripts shown
- [ ] package.yaml updated
- [ ] README.md auto-updated

---

## Deliverables

### Files Created
- `agent/patterns/mcp-server-starter.test-config.md`

### Files Modified
- `package.yaml`
- `README.md` (auto-updated)

---

**Previous Task**: [Task 6: Create Build Config Pattern](task-6-build-config-pattern.md)
**Next Task**: [Task 8: Create Config Management Pattern](task-8-config-management-pattern.md)
