# ACP Package: mcp-server-starter

TypeScript MCP server starter template with mcp-auth support and example tool

> **This package is designed for use with the [Agent Context Protocol](https://github.com/prmichaelsen/agent-context-protocol). Read more about ACP [here](https://github.com/prmichaelsen/agent-context-protocol).**

## Installation

### Quick Start (Bootstrap New Project)

Install ACP and this package in one command:

```bash
curl -fsSL https://github.com/prmichaelsen/acp-mcp-server-starter/raw/main/agent/scripts/bootstrap.sh | bash
```

This will:
1. Install ACP if not already installed
2. Install this package
3. Initialize your project with ACP

### Install Package Only (ACP Already Installed)

If you already have ACP installed in your project:

```bash
@acp.package-install https://github.com/prmichaelsen/acp-mcp-server-starter.git
```

Or using the installation script:

```bash
./agent/scripts/acp.package-install.sh https://github.com/prmichaelsen/acp-mcp-server-starter.git
```

## What's Included

<!-- ACP_AUTO_UPDATE_START:CONTENTS -->
### Commands

- **[`@mcp-server-starter.init`](agent/commands/mcp-server-starter.init.md)** - Initialize new MCP server project with complete setup
- **[`@mcp-server-starter.add-tool`](agent/commands/mcp-server-starter.add-tool.md)** - Generate new tool scaffolding with tests and registration

### Patterns

- **[`mcp-server-starter.bootstrap`](agent/patterns/mcp-server-starter.bootstrap.md)** - Project initialization and directory structure
- **[`mcp-server-starter.server-standalone`](agent/patterns/mcp-server-starter.server-standalone.md)** - Basic MCP server with stdio transport
- **[`mcp-server-starter.server-factory`](agent/patterns/mcp-server-starter.server-factory.md)** - Multi-tenant server with mcp-auth integration
- **[`mcp-server-starter.tool-creation`](agent/patterns/mcp-server-starter.tool-creation.md)** - MCP tool definition and implementation
- **[`mcp-server-starter.build-config`](agent/patterns/mcp-server-starter.build-config.md)** - esbuild configuration for dual builds
- **[`mcp-server-starter.test-config`](agent/patterns/mcp-server-starter.test-config.md)** - Jest configuration for TypeScript + ESM
- **[`mcp-server-starter.config-management`](agent/patterns/mcp-server-starter.config-management.md)** - Environment variable and configuration management

### Designs

- **[`mcp-server-starter.architecture`](agent/design/mcp-server-starter.architecture.md)** - Overall MCP server architecture and dual export pattern
- **[`mcp-server-starter.mcp-auth-integration`](agent/design/mcp-server-starter.mcp-auth-integration.md)** - Multi-tenant deployment with mcp-auth authentication
<!-- ACP_AUTO_UPDATE_END:CONTENTS -->

## Why Use This Package

This package provides everything you need to build production-ready MCP servers:

- **Complete Patterns**: 7 comprehensive patterns covering the entire development lifecycle
- **Automated Commands**: 2 commands to scaffold projects and generate tools
- **Architecture Guidance**: 2 design documents explaining when and how to use each pattern
- **Production Ready**: Includes multi-tenant support via mcp-auth
- **Type Safe**: Full TypeScript support with strict typing
- **Well Documented**: Every pattern includes complete code examples and anti-patterns

## Usage

### Initialize a New MCP Server Project

```bash
@mcp-server-starter.init
```

This creates a complete MCP server project with:
- TypeScript configuration
- Dual export pattern (standalone + factory)
- Example hello_computer tool
- Build and test configuration
- Git repository initialization

### Add a New Tool

```bash
@mcp-server-starter.add-tool --name search_documents
```

This generates:
- Tool definition with schema
- TypeScript interfaces
- Handler function template
- Test file
- Automatic server registration

## Development

### Setup

1. Clone this repository
2. Make changes
3. Run `@acp.package-validate` to validate
4. Run `@acp.package-publish` to publish

### Adding New Content

- Use `@acp.pattern-create` to create patterns
- Use `@acp.command-create` to create commands
- Use `@acp.design-create` to create designs

These commands automatically:
- Add namespace prefix to filenames
- Update package.yaml contents section
- Update this README.md

### Testing

Run `@acp.package-validate` to validate your package locally.

### Publishing

Run `@acp.package-publish` to publish updates. This will:
- Validate the package
- Detect version bump from commits
- Update CHANGELOG.md
- Create git tag
- Push to remote
- Test installation

## Namespace Convention

All files in this package use the `mcp-server-starter` namespace:
- Commands: `mcp-server-starter.command-name.md`
- Patterns: `mcp-server-starter.pattern-name.md`
- Designs: `mcp-server-starter.design-name.md`

## Dependencies

(List any required packages or project dependencies here)

## Local Development Directories

This package includes local-only directories for development workflow:

### Clarifications (`agent/clarifications/`)

Use this directory to document questions and clarifications during development:
- Create clarification documents using the template: `clarification-{N}-{title}.template.md`
- Document requirements gaps, design questions, and implementation decisions
- **Local by default**: Content files are gitignored, only `.gitkeep` is tracked
- **Optional tracking**: Remove patterns from `.gitignore` to track specific clarifications

### Feedback (`agent/feedback/`)

Use this directory to capture feedback during development:
- Document user feedback, bug reports, and feature requests
- Keep notes about what works and what needs improvement
- **Local by default**: Content files are gitignored, only `.gitkeep` is tracked
- **Optional tracking**: Remove patterns from `.gitignore` to track specific feedback

### Reports (`agent/reports/`)

Session reports and development logs:
- Automatically generated by `@acp.report` command
- **Local by default**: Content files are gitignored, only `.gitkeep` is tracked
- **Optional tracking**: Remove patterns from `.gitignore` to track specific reports

**Note**: These directories follow the same pattern - they exist in the repository structure (via `.gitkeep`), but their content is local-only by default. You can choose to track specific files by removing them from `.gitignore`.

## Contributing

Contributions are welcome! Please:

1. Follow the existing pattern structure
2. Use entity creation commands (@acp.pattern-create, etc.)
3. Run @acp.package-validate before committing
4. Document your changes in CHANGELOG.md
5. Test installation before submitting

## License

MIT

## Author

Patrick Michaelsen
