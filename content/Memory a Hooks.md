---
tags:
  - ai-workflow
---

# Memory a Hooks

Dvě věci, které řeší to, na co [[Prompting#CLAUDE.md|CLAUDE.md]] nestačí: přenos znalostí mezi sessions a automatické chování harnessu.

---

## Persistent memory

Claude Code si drží soubory s pamětí mimo repozitář:

```
~/.claude/projects/<projekt>/memory/
  MEMORY.md              ← index, načítá se každou session
  project_neco.md        ← jedna paměť = jeden soubor
  feedback_neco.md
```

Každá paměť je jeden fakt v jednom souboru s frontmatterem (`name`, `description`, `type`). `MEMORY.md` je index — jeden řádek na paměť, nikdy ne samotný obsah.

### Typy

| Typ | Obsah |
|-----|-------|
| `user` | Kdo jsem — role, expertiza, preference |
| `feedback` | Jak mám chtít pracovat — korekce i potvrzené postupy, včetně proč |
| `project` | Probíhající práce a omezení, které nejdou vyčíst z kódu |
| `reference` | Odkazy na externí zdroje — URL, dashboardy, tickety |

Paměti se propojují wikilinky `[[nazev]]`, stejně jako v Obsidianu.

### Co do paměti nepatří

Cokoliv, co už zaznamenává repozitář — struktura kódu, historie oprav, git log, CLAUDE.md. Paměť je na to, co je **nesamozřejmé** a co by se jinak ztratilo.

### Rozdíl oproti CLAUDE.md

| | CLAUDE.md | Memory |
|---|---|---|
| Rozsah | Projekt nebo globálně | Per projekt, mimo repo |
| Verzování | Commitnuté v gitu | Lokální, necommitnuté |
| Kdo píše | Já / AI vědomě | AI průběžně sám |
| Sdílení | Každý, kdo naklonuje repo | Jen já na daném stroji |

Proto se memory **nesynchronizuje** mezi stroji spolu se zbytkem konfigurace — je to lokální stav, ne konfigurace.

---

## Hooks

Hook je příkaz, který spustí **harness**, ne AI. To je zásadní rozdíl: cokoliv ve stylu „od teď pokaždé, když X" nejde vyřešit pamětí ani promptem — musí to být hook v `~/.claude/settings.json`.

```json
"hooks": {
  "SessionStart": [
    { "hooks": [{ "type": "command", "command": "node \"...\"" }] }
  ],
  "PostToolUse": [
    { "hooks": [{ "type": "command", "command": "node \"...\"" }] }
  ]
}
```

**Kdy hook a kdy prompt:** prompt je prosba, hook je záruka. Když na dodržení skutečně záleží, patří to do hooku.

---

## Další nastavení v settings.json

Věci, které stojí za zmínku:

| Klíč | K čemu |
|------|--------|
| `attribution` | Vypnutí co-authorship u commitů, viz [[Git Workflow#Co-authorship\|Co-authorship]] |
| `enabledPlugins` | Zapnutí/vypnutí pluginů bez odinstalace |
| `permissions.allow` | Allowlist nástrojů — méně potvrzovacích dialogů |
| `statusLine` | Vlastní status line — model, kontext, cena, branch |
| `outputStyle` | Styl odpovědí |
| `language` | Jazyk odpovědí |

Na úpravu settings.json existuje skill `update-config` — ruční editace JSONu s escapovanými shell příkazy je zbytečná bolest.

---

*Viz také: [[Context Management]], [[Prompting]], [[Globální CLAUDE.md]]*
