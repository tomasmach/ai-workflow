---
tags:
  - ai-workflow
---

# Globální CLAUDE.md

Můj globální konfigurační soubor pro Claude Code - uložen v `~/.claude/CLAUDE.md`.

Platí napříč **všemi projekty**. AI si ho přečte automaticky na začátku každé session.

Viz [[Prompting#CLAUDE.md|jak CLAUDE.md funguje]].

> Ekvivalent pro Codex je `~/.codex/AGENTS.md` — obsah držím synchronizovaný, viz [[Codex CLI#Globální AGENTS.md|AGENTS.md]].

---

## Obsah souboru

```markdown
# Global Claude Code Instructions

## Commit Message Guidelines

- Use conventional prefixes (`feat:`, `fix:`, `refactor:`, `docs:`, `test:`, `chore:`, `style:`, `perf:`), never scoped (`feat(scope):`)
- Single line, imperative mood: `feat: add user authentication`

## Tech Stack Preferences

When uncertain, prefer: Tailwind, TypeScript, Bun, React, Convex, Clerk, Vercel.

## Code Style

- Always strive for concise, simple solutions.
- If a problem can be solved in a simpler way, propose it.
- **UI descriptions:** Do not add subtitles, helper text, or descriptive copy beneath headings, labels, cards, or settings by default. Prefer one concise, self-explanatory heading or label. Only add supporting copy when the user explicitly asks for it or when it is necessary to prevent misunderstanding or error, and never use it to restate the heading.

## Planning

Invoke the `html-plan` skill when I explicitly request `/html-plan` or directly ask for an HTML plan. You may also invoke it selectively for a genuinely large feature that spans multiple subsystems and requires architectural decisions, migrations, or staged implementation. Do not invoke it for routine planning, localized changes, fixes, ordinary refactors, or merely because a task has multiple steps. When invoked, follow the skill's instructions and keep the terminal reply to a short summary + file path.

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

## Parallel Agent Usage

Always leverage parallel agents for better context management:

- **Use multiple agents simultaneously** - When facing 2+ independent tasks without shared state, deploy parallel agents instead of sequential execution
- **Maximize parallelization** - Independent operations (codebase exploration, multiple file reads, parallel testing) should run concurrently in a single message
- **Reduce context overhead** - Parallel execution avoids repeating context between sequential tasks and improves efficiency
- **Use appropriate agent types** - Combine specialized agents (Explore, Plan, test-runner, etc.) in parallel based on their independence

## General Preferences

- If asked to do too much work at once, stop and state that clearly.
- If computer use is helpful for completing or verifying work, shell out to gpt-5.6-sol with Codex for it.

## Picking the right models for workflows and subagents

Rankings, higher = better. Cost reflects what I actually pay, not list price.

| model       | cost | intelligence | taste |
|-------------|------|--------------|-------|
| gpt-5.6-sol | 7    | 9            | 7     |
| sonnet-5    | 5    | 5            | 7     |
| opus-4.8    | 4    | 7            | 8     |
| fable-5     | 2    | 9            | 9     |

How to apply:
- These are defaults, not limits. If a cheaper model's output doesn't meet the bar, redo the work with a smarter model without asking.
- Cost is a tie-breaker only; when axes conflict, intelligence > taste > cost.
- **Backend implementation: strongly prefer Codex (gpt-5.6-sol).** Route handlers, database/schema work, server logic, scripts, migrations, data processing, CLI tools — anything without a user-facing UI surface — goes through `codex exec` by default, even for small stuff.
- **Reading and investigation: also default to Codex.** `codex exec -s read-only` instead of inline. Cheap, and keeps raw file/log reading off Claude's context.
- Bulk/mechanical work: gpt-5.6-sol on low reasoning effort.
- Taste calls are the exception: UI, copy, and the *shape* of an API's public interface need taste ≥ 7.
- Reviews of plans/implementations: fable-5 or opus-4.8.
- **Never use Haiku — no exceptions, cost pressure included.**
- Codex reasoning effort: pick it per run with `-c model_reasoning_effort="<level>"`. Never above high.

(Následuje sekce o volání gpt-5.6-sol uvnitř workflows přes wrapper — detaily v [[Codex CLI]].)

## Error Policy

Always fix any errors you encounter during work - tests, lint, build, or runtime - even if they are pre-existing and unrelated to the current task. Never leave known broken tests or errors behind.
```

---

## Poznámky k jednotlivým sekcím

**Code Style** — pravidlo o UI descriptions je reakce na to, že modely automaticky doplňují vysvětlující text pod každý nadpis. Formulace „by default … only when explicitly asked" je záměrně děravá: bez té výjimky by AI odmítalo psát helper text i tam, kde je potřeba, třeba u destruktivní akce.

**Picking the right models** — nejdůležitější sekce souboru a jediná, kterou reálně průběžně ladím. Podrobně viz [[Výběr Modelu]].

**Error Policy** — krátká věta s velkým dopadem. Bez ní má AI tendenci obejít rozbitý test s poznámkou „tohle nesouvisí s mým taskem".

**Píšu anglicky** i když si nechávám odpovídat česky. Instrukce v angličtině fungují konzistentněji, jazyk odpovědi se řeší zvlášť v `settings.json`.

---

## Velikost

Soubor mám kolem 90 řádků a snažím se ho tam držet. Když naroste, řeknu AI ať ho zkrátí. Viz [[Prompting#Velikost CLAUDE.md|velikost CLAUDE.md]].

---

*Viz také: [[Prompting]], [[Výběr Modelu]], [[Git Workflow]], [[Codex CLI]], [[Memory a Hooks]]*
