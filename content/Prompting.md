---
tags:
  - ai-workflow
---

# Prompting

Jak psát prompty a jak konfigurovat AI pro konzistentní výsledky.

---

## Základní pravidla

### Piš anglicky

I když AI rozumí česky, anglické prompty dávají konzistentně lepší výsledky. Kód a technická terminologie jsou primárně anglické, česky psaný prompt vytváří zbytečné tření.

### Jasné a konkrétní zadání

- Popis **co** chceš, ne jak to má udělat
- Jeden task = jeden prompt (ne "udělej celý auth systém")
- Pokud si nejsi jistý jak to zadat, použij **Plan Mode** v Claude Code

### Menší tasky = lepší výsledky

Velký vágní task vede k horšímu kódu. Rozlož ho na konkrétní kroky.

---

## CLAUDE.md

Konfigurační soubor který AI přečte automaticky na začátku každé session.

### Globální CLAUDE.md

Uložen v `~/.claude/CLAUDE.md`, platí napříč všemi projekty.

Moje globální pravidla:
- Conventional commits formát
- Naming konvence pro branche
- Dependency management (vždy nejnovější verze)
- Python verze a package manager
- Jak volit modely pro paralelní agenty

### Repozitářový CLAUDE.md

Uložen v rootu projektu, platí jen pro daný repozitář.

**Jak ho vytvořit:** v Claude Code přes `/init`. Jiné nástroje mohou mít jiný příkaz.

Nechávám ho vytvořit AI samotného, on nejlépe ví co viděl v projektu.

**Commituju ho do gitu.** Kdokoliv kdo naklonuje repozitář a použije AI coding agent, automaticky dostane stejné guardrails. Není potřeba nic nastavovat zvlášť.

Typický obsah:
- Architektura projektu
- Použité konvence (naming, struktura souborů)
- Co nedělat / jak se vyhnout chybám specifickým pro projekt
- Tech stack a klíčové závislosti

### agents.md - ostatní nástroje

Claude používá `CLAUDE.md`, ale jiné AI nástroje (Codex, OpenCode...) hledají `agents.md`. Obsah je identický, jen název souboru se liší. Pokud pracuješ v multi-tool prostředí, je potřeba mít oba.

### Velikost CLAUDE.md

Studie naznačují, že kratší CLAUDE.md funguje lépe než delší. V praxi: nesnažím se ho mít extrémně velký. Když mi přijde že narostl moc, řeknu AI ať ho zmenší.

---

## Iterativní přístup

Prompting není jednorázová věc, je to konverzace.

- Dej AI feedback
- Upřesni co nesedí
- Přidej kontext když AI něco neví

Stejný přístup platí pro [[Plánování a Design Dokumenty#Design Dokument|Design dokumenty]].

---

*Viz také: [[Workflow Proces]], [[Plánování a Design Dokumenty]], [[Git Workflow]]*
