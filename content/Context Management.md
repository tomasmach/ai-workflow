---
tags:
  - ai-workflow
---

# Context Management

Každý AI model má omezený context window, tedy kolik textu "vidí" najednou. Efektivní práce s kontextem je klíč k tomu, aby AI dával kvalitní výstupy.

---

## Co je context window

- Představ si to jako pracovní paměť AI: vše co mu řekneš + vše co ti odpoví + obsah souborů, které čte
- Velikost se liší podle modelu a varianty, špička je dnes 1M tokenů
- Čím víc kontextu je zaplněného, tím víc se zhoršuje kvalita odpovědí, AI "ztrácí" důležité detaily
- Velký context window problém neřeší, jen posouvá. Kvalita klesá dávno předtím, než ho zaplníš

---

## Context compression

Když se kontext blíží limitu, AI automaticky provede "context compression". Starší části konverzace se shrnou do kratší verze, aby se uvolnilo místo. Funguje to, ale v tomhle bodě už AI často halucinuje a ztrácí důležité detaily. Lepší je začít novou session než se spoléhat na kompresi.

---

## Kdy začít novou session

- Když AI začne opakovat stejné chyby nebo zapomíná co jsi řekl dřív
- Když přecházíš na úplně jiný task, čistý kontext = lepší výsledky
- Po dokončení většího celku (feature, bugfix), nová session pro review

---

## Jak předávat kontext mezi sessions

- **CLAUDE.md** si AI čte automaticky na začátku každé session, proto tam patří architektura, konvence a pravidla projektu
- **Persistent memory** (`~/.claude/projects/<projekt>/memory/`) — poznámky napříč sessions, viz [[Memory a Hooks]]
- **Handoff notes**: u větších tasků si nech AI napsat shrnutí stavu před ukončením session (co je hotové, co zbývá, kde jsme skončili)
- **Design dokumenty a plány** slouží jako "kotva" pro kontext, AI si je přečte a ví kam směřuje

---

## Delegování jako nástroj správy kontextu

Nejúčinnější způsob, jak šetřit kontext, není psát kratší prompty — je nepustit si objemná data do kontextu vůbec.

- **Čtení a grepování deleguj na [[Codex CLI|Codex]]** (`codex exec -s read-only`). Vrátí ti závěr, ne stovky řádků souborů a logů
- **Subagenti mají vlastní kontext.** Jejich raw průzkum zůstane u nich, tobě přijde jen výsledek
- **Skill se načte až když je potřeba**, na rozdíl od CLAUDE.md, které zabírá místo pořád

---

## Tipy

- **Menší tasky = lepší výsledky**: rozděl práci na menší celky, každý v čisté session
- **Parallel agents** mají každý vlastní kontext, proto jsou efektivní na nezávislé úkoly
- **Plan Mode** pomáhá: AI nejdřív napíše plán (malý kontext), pak implementuje s jasným směrem
- Neposílej AI celý soubor, když potřebuješ změnit 3 řádky, buď specifický

---

*Viz také: [[Memory a Hooks]], [[Codex CLI]], [[Claude Code - Tipy a Triky]]*
