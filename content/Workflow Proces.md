---
tags:
  - ai-workflow
---

# Workflow Proces

Jak vypadá typický AI-driven development workflow od nápadu po merge.

---

## Malá featura

Pokud je featura malá a jasná:

1. Napiš prompt přímo do [[Nástroje#Claude Code|Claude Code]]
2. AI implementuje
3. Review, případné opravy
4. AI commituje a pushuje

Žádné plánování navíc, prostě to řekneš a jde se.

---

## Velká featura

Pokud je featura komplexní, vždy začínám plánováním.

```
Design dokument → Implementační plán → Implementace → Review
```

Podrobně viz [[Plánování a Design Dokumenty]].

---

## Git řídí AI

Veškerou git práci dělá AI sám, člověk pouze reviewuje:

- Vytváří nové branche
- Píše commit messages (conventional commits)
- Pushe na remote
- Vytváří Pull Requesty
- Opravuje testy které se rozbily

Viz [[Git Workflow]].

---

## Code Review a Simplify

Po implementaci vždy spouštím:

- **Code Review** - skill ze [[Claude Code - Tipy a Triky#Superpowers|Superpowers]] který zkontroluje kód
- **Simplify** - v Claude Code zabudovaný `/simplify`, v ostatních nástrojích skill ze Superpowers

---

## Princip

> Já řeším **co** se má udělat a **proč**. AI řeší **jak**.

---

*Viz také: [[Plánování a Design Dokumenty]], [[Prompting]], [[Git Workflow]]*
