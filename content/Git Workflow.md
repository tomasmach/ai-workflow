---
tags:
  - ai-workflow
---

# Git Workflow

AI řídí celý git workflow, člověk jen reviewuje.

---

## Co AI dělá automaticky

- Vytvoří novou branch před každou featurou
- Píše commit messages
- Pushuje na remote
- Vytváří Pull Request
- Opraví testy které se rozbily během implementace

Člověk pouze reviewuje PR a merguje.

---

## Naming konvence

### Branche

Prefix odpovídá typu práce:

```
feat/add-user-auth
fix/memory-leak
refactor/simplify-router
docs/update-api-docs
test/add-validation-tests
chore/update-dependencies
```

### Commit Messages

Conventional commits formát, jednořádkový, imperativ, bez scope:

```
feat: add user authentication
fix: resolve memory leak in cache
refactor: simplify database query logic
docs: update API documentation
test: add unit tests for validation
chore: update dependencies
```

**Nikdy:**
- `feat(scope): add search` - scopy nepoužívám
- víceřádkové commit messages

---

## Co-authorship

AI agenti (Claude Code, Codex...) se defaultně přidávají jako co-authors u commitů. Nelíbí se mi to, u commitu chci být napsaný jenom já.

V Claude Code se to vypne v `~/.claude/settings.json`:

```json
"attribution": {
  "commit": "",
  "pr": ""
}
```

---

## Cadence

Commituj a pushuj často — po každém uceleném kroku a vždy před přepnutím na jiný task.

Důvod je praktický: AI-driven development produkuje změny rychleji, než je stíháš reviewovat. Když necháš narůst velký nerozdělený diff, ztrácíš schopnost říct, který krok co rozbil.

---

## GitHub operace

Na práci s GitHubem (PR, issues, API) používám lokální `gh` CLI, ne GitHub MCP nebo API. Je to rychlejší a nezabírá to kontext popisem nástrojů.

---

## Globální git pravidla

V `~/.claude/CLAUDE.md` a `~/.codex/AGENTS.md` mám pravidla pro git, která platí napříč všemi projekty:

- Conventional commits formát, žádné scopy
- Naming konvence pro branche
- Commit a push často
- Nikdy necommitovat na default branch — nejdřív vytvořit branch

AI si tato pravidla přečte automaticky a drží se jich. **Musí být v obou souborech** — viz [[Prompting#AGENTS.md - ostatní nástroje|AGENTS.md]].

Viz [[Globální CLAUDE.md]].

---

*Viz také: [[Workflow Proces]], [[Prompting]], [[Globální CLAUDE.md]]*
