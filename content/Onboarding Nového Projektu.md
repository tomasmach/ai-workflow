---
tags:
  - ai-workflow
---

# Onboarding Nového Projektu

Jak připravit nový projekt pro AI-driven development od nuly.

---

## 1. Style Guide

Vytvoř si style guide pro programovací jazyk, ve kterém budeš psát. Definuj konvence, formátování, naming. Ulož ho jako dokument v repozitáři a odkaz na něj dej do CLAUDE.md.

---

## 2. Brainstorming

Než začneš cokoliv psát, prozkoumej s AI, co vlastně stavíš:

- Co má aplikace umět
- Co by **neměla** umět (tohle je stejně důležité)
- Jaké jsou omezení a constraints
- Kdo je cílový uživatel

Nech AI klást otázky. Viz [[Plánování a Design Dokumenty#Design Dokument|design dokument]].

---

## 3. Design Dokument

Vytvoř podrobný design dokument, kde projdeš co nejvíc do detailů:

- Architektura a tech stack
- Klíčové features a jejich chování
- Data model
- API design
- Edge cases a error handling

Viz [[Plánování a Design Dokumenty]] pro detaily o procesu.

---

## 4. Rozepsání do tasků

Velký design dokument rozděl na menší, konkrétní tasky:

- Každý task by měl být dostatečně malý na jednu AI session
- Jasně definovaný vstup a výstup
- Postupně je láduj do AI, task po tasku

---

## 5. CLAUDE.md projektu

CLAUDE.md moc neupravuješ ručně. AI si ho vytvoří a spravuje sám (`/init`). Důležité dokumenty (style guide, design doc, architektura) drž jako samostatné soubory v repozitáři a v CLAUDE.md na ně pouze odkazuj.

Pokud v projektu budeš používat i [[Codex CLI|Codex]] — u backendu skoro jistě ano — potřebuješ vedle toho `AGENTS.md` se stejným obsahem. Viz [[Prompting#agents.md - ostatní nástroje|AGENTS.md]].

---

## 6. Projektové skills

Postupy specifické pro daný projekt — jak spustit aplikaci, jak nasadit, jak se testuje — patří do `.claude/skills/` v repozitáři. Commitnou se do gitu, takže je dostane každý, kdo repo naklonuje.

Je to lepší místo než CLAUDE.md: skill se načte jen když je potřeba, zatímco CLAUDE.md zabírá kontext v každé session. Viz [[Skills#Skope|scope skills]].

---

## TL;DR

> Style Guide → Brainstorming → Design Doc → Tasky → Implementace po částech
