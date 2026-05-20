# Terminal App Builder Skill

Codex skill for generating production-quality local terminal applications with disciplined JavaScript, keyboard-first UX, tests, linting, and maintainable architecture.

## Install

### Option 1: Install With Codex

In Codex, ask the built-in skill installer to install this skill from GitHub:

```text
Use $skill-installer to install the skill from this GitHub repository:
https://github.com/<owner>/<repo>
```

Replace `https://github.com/<owner>/<repo>` with the URL of the repository containing this skill. Restart Codex after installation so the new skill is discovered.

If the skill lives inside a subdirectory of a larger repository, include the path:

```text
Use $skill-installer to install the skill from this GitHub repository path:
https://github.com/<owner>/<repo>/tree/main/path/to/terminal-app-builder
```

### Option 2: Manual Install

Manual installation is useful if you want to inspect or edit the skill locally.

Clone the repository into your Codex skills directory:

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
git clone https://github.com/<owner>/<repo>.git "${CODEX_HOME:-$HOME/.codex}/skills/terminal-app-builder"
```

If you already cloned it elsewhere, copy or symlink the skill folder into your Codex skills directory:

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
ln -s /path/to/terminal-app-builder "${CODEX_HOME:-$HOME/.codex}/skills/terminal-app-builder"
```

Codex discovers skills by reading folders under `$CODEX_HOME/skills`, or `~/.codex/skills` when `CODEX_HOME` is unset. The required file is `SKILL.md`; the `references/` folder contains the detailed terminal app standards loaded by the skill.

Restart Codex after installing or updating the skill.

## Use

Start Codex in the workspace where you want the new app created, then invoke the skill explicitly:

```text
Use $terminal-app-builder to create a local terminal app for managing warehouse stock adjustments.
```

You can also describe the app in more detail:

```text
Use $terminal-app-builder to create a keyboard-first terminal CRM for account managers. It should support customer search, account notes, task tracking, and a dense table view. Use pure JavaScript, npm scripts, tests, and linting.
```

The skill instructs Codex to produce a complete runnable project with:

- local terminal-first runtime
- pure JavaScript with JSDoc typing
- ECMAScript modules
- keyboard-first workflows
- deterministic focus and command behavior
- tests and linting
- README setup instructions
- quality verification commands

## Example: Simple Todo App Prompt

From the parent directory where you want the todo app project created, prompt Codex with:

```text
Use $terminal-app-builder to create a simple local terminal todo app in a new folder named terminal-todo.

Requirements:
- Use pure JavaScript with ECMAScript modules and JSDoc types.
- The app should run from the terminal with npm scripts.
- Support adding todos, listing todos, marking todos complete, deleting todos, and searching todos.
- Store todos locally in a JSON file.
- Provide a keyboard-first interactive mode with deterministic commands.
- Include useful CLI help text.
- Include ESLint and a test suite.
- Ensure npm test and npm run lint pass.
```

Codex should generate the complete project, install dependencies when needed, run the verification commands, and report the resulting run/test commands.

## Validate This Skill

If you are editing the skill itself, run the official validator:

```bash
python3 /path/to/skill-creator/scripts/quick_validate.py /path/to/terminal-app-builder
```
