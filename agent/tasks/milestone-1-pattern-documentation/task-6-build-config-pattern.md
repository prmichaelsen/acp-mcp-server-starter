# Task 6: Create Build Config Pattern

**Milestone**: M1 - Pattern Documentation
**Estimated Time**: 2-3 hours
**Dependencies**: Task 2 (Bootstrap Pattern)
**Status**: Not Started

---

## Objective

Create the build configuration pattern document that shows developers how to set up esbuild for dual builds (standalone + factory) with TypeScript declarations.

---

## Context

The build pattern uses esbuild for fast, efficient bundling:
- Dual build: server.js + server-factory.js
- ESM format with node20 target
- External dependencies (not bundled)
- CommonJS compatibility banner
- Separate TypeScript declaration generation

This enables both standalone and library usage of the MCP server.

---

## Steps

### 1. Review Analysis Document

Read "Pattern 4: Build Configuration (esbuild)" in [`agent/design/remember-mcp-analysis.md`](../../design/remember-mcp-analysis.md).

### 2. Create Pattern Document

Create `agent/patterns/mcp-server-starter.build-config.md`.

**Sections to Include**:
- **Overview**: Why esbuild for MCP servers
- **Core Principles**: Fast builds, ESM, dual output
- **Dual Build Pattern**: Server + factory builds
- **esbuild Configuration**: Complete config walkthrough
- **External Dependencies**: What to bundle vs external
- **TypeScript Declarations**: tsc --emitDeclarationOnly
- **npm Scripts**: dev, build, build:watch
- **Examples**: Complete esbuild.build.js
- **Benefits**: Speed and flexibility
- **Anti-Patterns**: Common config mistakes

### 3. Add Complete esbuild.build.js Example

Include complete build script with:
- Server build configuration
- Factory build configuration
- TypeScript declaration generation
- Error handling

### 4. Document npm Scripts

Show package.json scripts:
```json
{
  "scripts": {
    "build": "node esbuild.build.js",
    "build:watch": "node esbuild.watch.js",
    "dev": "tsx watch src/server.ts",
    "start": "node dist/server.js",
    "prepublishOnly": "npm run clean && npm run build"
  }
}
```

### 5. Explain External Dependencies

Document which dependencies should be external:
- @modelcontextprotocol/sdk (always external)
- Database clients (usually external)
- Large libraries (case-by-case)

### 6. Update package.yaml

Add pattern to contents.patterns array.

---

## Verification

- [ ] Pattern document created
- [ ] Complete esbuild.build.js example included
- [ ] Dual build pattern explained
- [ ] npm scripts documented
- [ ] External dependencies guidance provided
- [ ] package.yaml updated
- [ ] README.md auto-updated

---

## Deliverables

### Files Created
- `agent/patterns/mcp-server-starter.build-config.md`

### Files Modified
- `package.yaml`
- `README.md` (auto-updated)

---

**Previous Task**: [Task 5: Create Tool Creation Pattern](task-5-tool-creation-pattern.md)
**Next Task**: [Task 7: Create Test Config Pattern](task-7-test-config-pattern.md)
