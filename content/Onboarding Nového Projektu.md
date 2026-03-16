---
tags:
  - ai-workflow
---

# Onboarding Nového Projektu

Jak připravit nový projekt pro AI-driven development od nuly.

---

## 1. Style Guide

Vytvoř si style guide pro programovací jazyk, ve kterém budeš psát. Definuj konvence, formátování, naming — vše co má AI dodržovat. Toto jde rovnou do CLAUDE.md projektu.

---

## 2. Brainstorming

Použij [[Pluginy a Rozšíření|Superpowers brainstorming skill]] k prozkoumání toho, co vlastně budeš stavět:

- Co má aplikace umět
- Co by **neměla** umět (tohle je stejně důležité)
- Jaké jsou omezení a constraints
- Kdo je cílový uživatel

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
- Postupně je láduj do AI — task po tasku

---

## 5. CLAUDE.md projektu

Na základě style guide a design dokumentu vytvoř repozitářový CLAUDE.md:

- Architektura projektu
- Konvence a pravidla
- Co nedělat (anti-patterns)

AI si ho přečte automaticky na začátku každé session a drží se definovaných pravidel.

---

## TL;DR

> Style Guide → Brainstorming → Design Doc → Tasky → Implementace po částech
