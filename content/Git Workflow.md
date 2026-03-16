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

## CLAUDE.md - Globální Git Pravidla

V globálním `CLAUDE.md` mám definovaná pravidla pro git která platí napříč všemi projekty:

- Conventional commits formát
- Žádné scopy
- Naming konvence pro branche
- AI musí vždy commitovat, pushovat a vytvářet PR

AI si tato pravidla přečte automaticky a drží se jich.

Viz [[Prompting#CLAUDE.md|CLAUDE.md]].

---

*Viz také: [[Workflow Proces]], [[Prompting]]*
