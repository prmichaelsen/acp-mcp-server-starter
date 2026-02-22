# Task 13: Build Example Starter Template

**Milestone**: M3 - Package Validation & Publishing
**Estimated Time**: 3-4 hours
**Dependencies**: Milestone 2 (All patterns, commands, and designs completed)
**Status**: Not Started

---

## Objective

Build a minimal working MCP server example that demonstrates all patterns in practice. This serves as both a reference implementation and a testing artifact for package validation.

---

## Context

The example template should:
- Demonstrate all documented patterns
- Include hello_computer tool
- Be minimal but complete
- Work out of the box
- Serve as installation test artifact

This validates that all patterns work together correctly.

---

## Steps

### 1. Decide on Example Location

Choose where to build the example:
- **Option A**: Separate `example/` directory in package (not installed)
- **Option B**: Temporary directory for testing only
- **Option C**: Skip if patterns are sufficient

**Recommendation**: Option B (temporary, for testing only)

### 2. Create Example Project Structure

If building example:
```
/tmp/mcp-server-example/
├── src/
│   ├── server.ts
│   ├── server-factory.ts
│   ├── config.ts
│   └── tools/
│       └── hello-computer.ts
├── package.json
├── tsconfig.json
├── esbuild.build.js
├── jest.config.js
└── .env.example
```

### 3. Implement All Files

Create each file following the documented patterns:
- Use patterns as reference
- Ensure all code is complete and working
- Include comments referencing patterns

### 4. Test the Example

Verify the example works:
```bash
cd /tmp/mcp-server-example
npm install
npm run build
npm test
node dist/server.js
```

### 5. Document Example Usage

If keeping example, create README:
- How to run the example
- What it demonstrates
- How to extend it

### 6. Clean Up

If temporary:
- Use example for testing
- Delete after validation
- Document that patterns are the source of truth

---

## Verification

- [ ] Example project structure created (if applicable)
- [ ] All files implemented following patterns
- [ ] Example builds successfully
- [ ] Example tests pass
- [ ] Example runs without errors
- [ ] hello_computer tool works
- [ ] Example demonstrates all patterns
- [ ] Documentation complete (if keeping)

---

## Deliverables

### Files Created (if keeping example)
- `example/` directory with complete MCP server

### Files Modified
- None (example is standalone)

---

## Notes

- **Primary Goal**: Validate that patterns work together
- **Secondary Goal**: Provide reference implementation
- **Decision**: Can skip if confident in patterns
- Consider creating example in separate repository instead

---

**Previous Task**: [Task 12: Create mcp-auth Integration Design Document](../../milestone-2-command-design-documentation/task-12-mcp-auth-integration-design.md) (Milestone 2)
**Next Task**: [Task 14: Validate Package and Test Installation](task-14-validate-and-test.md)
