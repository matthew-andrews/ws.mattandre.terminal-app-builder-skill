---
name: terminal-app-builder
description: Generate complete, production-quality full-screen ANSI/TUI applications that run from the terminal and replace the interactive shell prompt with a keyboard-driven menu workspace. Use when Codex is asked to create, scaffold, or substantially implement a terminal-native app, DOS/Sage Line 50-style menu system, keyboard-first operational system, local-first JavaScript application, or enterprise-style terminal interface with tests, linting, typed JavaScript, and maintainable architecture. Do not treat this as a simple command tool or flag-driven CLI unless the user explicitly asks for that.
---

# Terminal App Builder

Use this skill to create complete local-first terminal applications that are runnable immediately and engineered for expert keyboard operators.

The default output is a full-screen ANSI/TUI application: it should take over the terminal, draw stable screens and menus, and keep the user inside an interactive workspace similar to DOS-era business software, Sage Line 50, AS/400 systems, Bloomberg Terminal, or airline reservation terminals. Do not default to a command-line utility that prints help text, accepts flags, and exits. Build that style only when the user explicitly asks for a simple CLI command.

Before implementation, read [terminal-app-standards.md](references/terminal-app-standards.md). It contains the UX philosophy, engineering rules, JavaScript standards, testing expectations, and response requirements for generated applications.

## Core Workflow

1. Clarify only blocking product details. If the user leaves details open, choose conservative defaults that fit the requested domain and the terminal-app standards.
2. Design the app as screens, panels, focus regions, command contexts, forms, menus, and grids, not as shell commands or web pages.
3. Select the smallest stable dependency set that can satisfy the requested terminal experience. Prefer Blessed, Ink, or other TUI-capable libraries for full-screen interfaces; use Commander only for launch commands, setup commands, or explicitly requested simple CLIs.
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
- full-screen ANSI rendering and redraw boundaries
- menu hierarchy and selection state
- form and validation flow
- grid/table navigation
- status and notification output
- condition-specific domain error classes
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
- useful error messages and intentional handling of anticipated failures

Use tabs for indentation in generated JavaScript and project files where indentation is relevant. Use US English spelling.

## Terminal UX Requirements

Prioritize keyboard-first, dense, predictable operation:

- `UP` and `DOWN` highlight menu options, rows, and list items without triggering them
- `ENTER` opens the highlighted menu option, confirms a selection, or advances to the next input field depending on context
- `ESC` goes back to the previous menu, closes the active popup, cancels the current operation, or moves to the previous field in data-entry contexts
- deterministic `TAB` and `SHIFT+TAB` focus movement where tab-style navigation is appropriate
- `ENTER` for confirm or advance
- arrow keys for movement
- function keys for primary workflows when the chosen library and terminal environment support them
- incremental search wherever records or command lists are navigated
- stable layouts with header, navigation, main content, status, and command regions
- a persistent full-screen application frame rather than a prompt-response loop

Treat common business controls as rich terminal widgets, not plain text prompts:

- menus with highlighted selection, accelerator keys, nested screens, and breadcrumbs or status context
- multi-field input screens with labels, validation messages, current-field highlighting, and rapid `ENTER`-to-next-field data entry
- date fields that open a popup date picker with month navigation, day selection, cancel/back behavior, and clear focus trapping
- lookup fields that open searchable popup lists or grids
- confirmation, error, and selection dialogs that are keyboard navigable and visually distinct

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
