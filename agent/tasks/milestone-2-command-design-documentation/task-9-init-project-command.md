# Task 9: Create init-project Command

**Milestone**: M2 - Command & Design Documentation
**Estimated Time**: 3-4 hours
**Dependencies**: Milestone 1 (All patterns completed)
**Status**: Not Started

---

## Objective

Create the init-project command document that provides a workflow for initializing a new MCP server project with all necessary files and configuration.

---

## Context

The init-project command automates project scaffolding by:
- Creating directory structure
- Generating configuration files
- Installing dependencies
- Setting up git repository
- Creating example tool (hello_computer)

This command makes it easy for developers to start new MCP server projects.

---

## Steps

### 1. Review Related Patterns

Read these patterns for context:
- [`mcp-server-starter.bootstrap`](../../patterns/mcp-server-starter.bootstrap.md) (if exists)
- [`mcp-server-starter.server-standalone`](../../patterns/mcp-server-starter.server-standalone.md) (if exists)
- [`mcp-server-starter.tool-creation`](../../patterns/mcp-server-starter.tool-creation.md) (if exists)

### 2. Create Command Document

Create `agent/commands/mcp-server-starter.init-project.md` using the command template.

**Sections to Include**:
- **Purpose**: Initialize new MCP server project
- **Prerequisites**: Node.js, npm, git
- **Steps**: Complete workflow with actions and expected outcomes
- **Verification**: Checklist of what should exist
- **Expected Output**: Files created and console output
- **Examples**: Usage scenarios
- **Troubleshooting**: Common issues
- **Security Considerations**: File access, network, secrets

### 3. Define Command Steps

Document the complete workflow:

1. **Gather Project Information**
   - Project name
   - Description
   - Author
   - License

2. **Create Directory Structure**
   ```
   project-name/
   ├── src/
   │   ├── tools/
   │   └── utils/
   ├── tests/
   └── dist/
   ```

3. **Generate Configuration Files**
   - package.json
   - tsconfig.json
   - esbuild.build.js
   - esbuild.watch.js
   - jest.config.js
   - .env.example
   - .gitignore

4. **Create Server Files**
   - src/server.ts (standalone)
   - src/server-factory.ts (factory)
   - src/config.ts

5. **Create Example Tool**
   - src/tools/hello-computer.ts

6. **Initialize Git**
   - git init
   - Initial commit

7. **Install Dependencies**
   - npm install

8. **Provide Next Steps**
   - How to run dev server
   - How to build
   - How to test

### 4. Add Complete File Templates

Include templates for all generated files (or reference patterns).

### 5. Document Command Invocation

Show how users invoke the command:
```bash
@mcp-server-starter.init-project
```

Or with arguments:
```bash
@mcp-server-starter.init-project --name my-server --author "John Doe"
```

### 6. Update package.yaml

Add command to contents.commands array:
```yaml
contents:
  commands:
    - name: init-project
      file: mcp-server-starter.init-project.md
      description: Initialize new MCP server project
```

---

## Verification

- [ ] Command document created
- [ ] All steps documented with actions and outcomes
- [ ] File templates included or referenced
- [ ] Invocation examples provided
- [ ] Troubleshooting section complete
- [ ] package.yaml updated
- [ ] README.md auto-updated

---

## Deliverables

### Files Created
- `agent/commands/mcp-server-starter.init-project.md`

### Files Modified
- `package.yaml`
- `README.md` (auto-updated)

---

**Previous Task**: [Task 8: Create Config Management Pattern](../../milestone-1-pattern-documentation/task-8-config-management-pattern.md) (Milestone 1)
**Next Task**: [Task 10: Create add-tool Command](task-10-add-tool-command.md)
