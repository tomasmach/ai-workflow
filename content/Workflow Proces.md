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

- **`/code-review`** - zkontroluje pracovní diff, hledá chyby
- **`/simplify`** - zjednoduší napsaný kód, odstraní zbytečnou komplexitu

Obojí je v Claude Code zabudované. Na nezávislý druhý pohled navíc pouštím `codex review`, viz [[Codex CLI]].

---

## Volba modelu

Ještě než začne implementace, rozhodni **kdo ji odvede**. U backendu je odpověď skoro vždy [[Codex CLI|Codex]], u UI naopak model s taste.

Špatná volba modelu je dražší než špatný prompt — prompt opravíš v další zprávě, špatně napsaný kód reviewuješ, přepisuješ a stejně ti část projde.

Viz [[Výběr Modelu]].

---

## Princip

> Já řeším **co** se má udělat a **proč**. AI řeší **jak**.

---

*Viz také: [[Plánování a Design Dokumenty]], [[Výběr Modelu]], [[Prompting]], [[Git Workflow]]*
