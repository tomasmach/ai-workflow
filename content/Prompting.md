---
tags:
  - ai-workflow
---

# Prompting

Jak psát prompty a jak konfigurovat AI pro konzistentní výsledky.

---

## Základní pravidla

### Instrukce piš anglicky

Konfigurační soubory (`CLAUDE.md`, `AGENTS.md`, skills) píšu vždy anglicky — pravidla v angličtině fungují konzistentněji, kód a technická terminologie jsou stejně anglické.

**Jazyk odpovědi je něco jiného.** Ten se řeší zvlášť v `settings.json` (`"language": "czech"`) a s kvalitou instrukcí nesouvisí. Můžeš mít anglická pravidla a české odpovědi.

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
- Conventional commits formát a naming konvence pro branche
- Preferovaný tech stack
- Code style, včetně pravidla proti automatickému doplňování popisků v UI
- Dependency management (vždy nejnovější verze)
- Python verze a package manager
- [[Výběr Modelu|Jak volit modely]] pro workflows a subagenty
- Error policy — opravit i chyby, které s taskem nesouvisí

Celý obsah viz [[Globální CLAUDE.md]].

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

### AGENTS.md - ostatní nástroje

`AGENTS.md` je totéž co `CLAUDE.md` - stejný formát, stejný obsah. Jediný rozdíl je v názvu souboru. Claude Code čte `CLAUDE.md`, prakticky všechny ostatní nástroje (Codex, OpenCode, Cursor, Windsurf...) čtou `AGENTS.md`. Pokud pracuješ s víc nástroji, potřebuješ oba.

Platí to i globálně: `~/.claude/CLAUDE.md` a `~/.codex/AGENTS.md`.

**Držet je synchronizované je nutnost, ne kosmetika.** Když backend a investigace jdou defaultně přes [[Codex CLI|Codex]], pravidlo, které je jen v CLAUDE.md, fakticky neplatí pro polovinu práce. Typický způsob, jak si tenhle problém způsobit: přidáš pravidlo do CLAUDE.md, pak se divíš, proč ho Codex ignoruje.

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

*Viz také: [[Globální CLAUDE.md]], [[Skills]], [[Memory a Hooks]], [[Workflow Proces]], [[Git Workflow]]*
