---
tags:
  - ai-workflow
---

# Globální CLAUDE.md

Můj globální konfigurační soubor pro Claude Code — uložen v `~/.claude/CLAUDE.md`.

Platí napříč **všemi projekty**. AI si ho přečte automaticky na začátku každé session.

Viz [[Prompting#CLAUDE.md|jak CLAUDE.md funguje]].

---

## Obsah souboru

```markdown
# Global Claude Code Instructions

## Commit Message Guidelines

Always follow these rules when creating git commits:

- **Use conventional commit prefixes**: `feat:`, `fix:`, `refactor:`, `docs:`, `test:`, `chore:`, `style:`, `perf:`
- **Never add scopes** - do NOT use `feat(scope):` format, only use simple `feat:` format
- **Never modify or extend existing prefixes** - if a prefix exists, use it as-is without additions
- **Keep commits to a single line** - no multi-line commit messages
- **Be concise and descriptive** - explain what changed, not why
- **Use imperative mood** - "add feature" not "added feature"

Examples of correct format:
- `feat: add user authentication`
- `fix: resolve memory leak in cache`
- `refactor: simplify database query logic`
- `docs: update API documentation`
- `test: add unit tests for validation`
- `chore: update dependencies`

Examples of INCORRECT format (never use):
- `feat(AI-Search): add search`
- `fix(auth): resolve bug`
- `refactor(database): simplify query`

## Branch Naming

Use prefixes matching commit types: `feat/`, `fix/`, `refactor/`, `docs/`, `test/`, `chore/`. Examples:
- `feat/add-web-search`
- `fix/memory-leak`
- `refactor/simplify-router`

## Dependency Management

Always follow this rule when adding dependencies in any programming language:

- **Check for newest versions** - before adding any requirement, package, or dependency, always check for and use the newest available version

## Python Development Guidelines

Always follow these rules when working with Python:

- **Always use UV** - use UV for package management and virtual environment handling
- **Use Python 3.14** - ensure all Python projects use Python 3.14

## Parallel Subagent Model Selection

When deploying parallel subagents, always evaluate task difficulty and choose the appropriate model:

- **Sonnet** - the default model for most work (code implementation, refactoring, debugging, multi-step operations, general development tasks)
- **Haiku** - only for very simple tasks where Sonnet would be overkill (basic file reading, trivial searches, simple one-line edits)
- **Opus** - reserve for only the hardest, most complex tasks (sophisticated architectural decisions, extremely difficult debugging, intricate system-wide refactoring, advanced algorithm design)

Default to Sonnet for most tasks. Only choose Haiku when the task is trivially simple, and only choose Opus when the task is exceptionally complex and clearly beyond Sonnet's capabilities.

## Parallel Agent Usage

Always leverage parallel agents for better context management:

- **Use multiple agents simultaneously** - When facing 2+ independent tasks without shared state, deploy parallel agents instead of sequential execution
- **Maximize parallelization** - Independent operations (codebase exploration, multiple file reads, parallel testing) should run concurrently in a single message
- **Reduce context overhead** - Parallel execution avoids repeating context between sequential tasks and improves efficiency
- **Use appropriate agent types** - Combine specialized agents (Explore, Plan, test-runner, etc.) in parallel based on their independence

## Bug Reports

When you receive a bug report:

1. **Write a test first** - Create a test that reproduces the bug before attempting any fixes
2. **Have subagents fix it** - Deploy parallel subagents to attempt fixes while you monitor
3. **Prove it with tests** - Require that the bug fix is validated by the passing test before considering it resolved

This ensures the bug is truly reproducible, fixes are evidence-based, and regressions are prevented.
```

---

*Viz také: [[Prompting]], [[Git Workflow]], [[Claude Code - Tipy a Triky]]*
