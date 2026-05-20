---
name: terminal-app-builder
description: Generate complete, production-quality local applications that run from the terminal. Use when Codex is asked to create, scaffold, or substantially implement a terminal-driven app, TUI, CLI workflow tool, keyboard-first operational system, local-first JavaScript application, or enterprise-style terminal interface with tests, linting, typed JavaScript, and maintainable architecture.
---

# Terminal App Builder

Use this skill to create complete local-first terminal applications that are runnable immediately and engineered for expert keyboard operators.

Before implementation, read [terminal-app-standards.md](references/terminal-app-standards.md). It contains the UX philosophy, engineering rules, JavaScript standards, testing expectations, and response requirements for generated applications.

## Core Workflow

1. Clarify only blocking product details. If the user leaves details open, choose conservative defaults that fit the requested domain and the terminal-app standards.
2. Design the app as screens, panels, focus regions, command contexts, forms, and grids, not as web pages.
3. Select the smallest stable dependency set that can satisfy the requested terminal experience. Prefer native Node.js APIs for simple CLIs; use Commander, Chalk, Ink, or Blessed only when they materially improve the app.
4. Generate the full project structure, including `package.json`, source files, tests, linting configuration, and README instructions.
5. Use native ECMAScript modules and pure JavaScript with JSDoc typing. Do not require TypeScript compilation unless the user explicitly asks for TypeScript.
6. Implement real behavior. Do not leave core workflows as pseudo-code, placeholders, or TODO-driven stubs.
7. Verify the project locally. Run install, lint, tests, and a startup or CLI smoke check when feasible.

## Architecture Expectations

Build around explicit, reusable primitives:

- command registry and command execution
- keyboard routing
- focus management
- stable layout regions
- form and validation flow
- grid/table navigation
- status and notification output
- expected domain error classes
- clear module boundaries

Keep state transitions explicit and deterministic. Treat performance, startup speed, and immediate keyboard response as core UX requirements.

## Generated Project Baseline

Every generated app must include:

- `package.json` with runnable scripts
- source modules with explicit imports and exports
- JSDoc types or dedicated type definition files where appropriate
- ESLint or an equivalent lint setup
- Vitest, Node.js test runner, or another appropriate test runner
- representative tests for domain logic, validation, and CLI/TUI behavior
- README with setup, run, development, and verification commands
- useful error messages and intentional handling of expected failures

Use tabs for indentation in generated JavaScript and project files where indentation is relevant. Use US English spelling.

## Terminal UX Requirements

Prioritize keyboard-first, dense, predictable operation:

- deterministic `TAB` and `SHIFT+TAB` focus movement
- `ENTER` for confirm or advance
- `ESC` for cancel or back
- arrow keys for movement
- function keys for primary workflows when the chosen library and terminal environment support them
- incremental search wherever records or command lists are navigated
- stable layouts with header, navigation, main content, status, and command regions

Make the active focus region visually obvious. Ensure focus never feels lost, especially inside dialogs or modal flows.

## Verification

Before final response, run the available quality gates:

```bash
npm test
npm run lint
```

Also run the main command or a representative smoke test, such as:

```bash
npm start
node ./bin/<command>.js --help
```

If a verification step cannot run because dependencies cannot be installed, network access is unavailable, or the user declined approval, state that clearly in the final response.
