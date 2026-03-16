---
tags:
  - ai-workflow
---

# Context Management

Každý AI model má omezený context window, tedy kolik textu "vidí" najednou. Efektivní práce s kontextem je klíč k tomu, aby AI dával kvalitní výstupy.

---

## Co je context window

- Představ si to jako pracovní paměť AI: vše co mu řekneš + vše co ti odpoví + obsah souborů, které čte
- Opus 4.6: 1M tokenů, Sonnet 4.6: 200k tokenů
- Čím víc kontextu je zaplněného, tím víc se zhoršuje kvalita odpovědí, AI "ztrácí" důležité detaily

---

## Kdy začít novou session

- Když AI začne opakovat stejné chyby nebo zapomíná co jsi řekl dřív
- Když přecházíš na úplně jiný task, čistý kontext = lepší výsledky
- Po dokončení většího celku (feature, bugfix), nová session pro review

---

## Jak předávat kontext mezi sessions

- **CLAUDE.md** si AI čte automaticky na začátku každé session, proto tam patří architektura, konvence a pravidla projektu
- **Memory system** v Claude Code má persistent memory (`~/.claude/projects/`), kam si ukládá poznámky napříč sessions
- **Handoff notes**: u větších tasků si nech AI napsat shrnutí stavu před ukončením session (co je hotové, co zbývá, kde jsme skončili)
- **Design dokumenty a plány** slouží jako "kotva" pro kontext, AI si je přečte a ví kam směřuje

---

## Tipy

- **Menší tasky = lepší výsledky**: rozděl práci na menší celky, každý v čisté session
- **Parallel agents** mají každý vlastní kontext, proto jsou efektivní na nezávislé úkoly
- **Plan Mode** pomáhá: AI nejdřív napíše plán (malý kontext), pak implementuje s jasným směrem
- Neposílej AI celý soubor, když potřebuješ změnit 3 řádky, buď specifický
