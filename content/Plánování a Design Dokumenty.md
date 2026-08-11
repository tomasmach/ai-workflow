---
tags:
  - ai-workflow
---

# Plánování a Design Dokumenty

Jak přistupovat k plánování větších featur a projektů.

---

## Kdy plánovat

- **Malá featura** → rovnou implementace, žádný plán
- **Velká featura / nový projekt** → vždy začít design dokumentem

---

## Design Dokument

Iterativní dokument který vytváříš **společně s AI**.

**Postup:**
1. Popiš AI záměr a nech ho ptát se na to, co není jasné
2. AI klade otázky, ty odpovídáš
3. Iteruj dokud nemáš jasno
4. Výsledek uložíš jako design doc

Klíčová část je ta druhá: nutit AI klást otázky, ne rovnou navrhovat. Když skočí rovnou k řešení, dostaneš pěkně napsaný dokument o něčem, co jsi nechtěl.

Cíl: mít jasno v tom **co** buduješ předtím, než se začne psát kód.

### Příklad: Design dokument

Zkrácený příklad reálného design docu (z projektu Vespra -Discord bot s pamětí):

```markdown
# Memory Improvements Design

## Problem
With 90+ memories on a server, the bot:
1. Can't find memories it already has
2. Saves duplicate/similar memories

## Solution Overview
Four changes: dedup-on-save, better recall filtering, FTS5 search, smarter auto-recall.

## 1. Dedup-on-Save
When Save() is called, before inserting:
1. Embed the new memory content
2. Find similar memories (cosine similarity >= 0.85)
3. If match found and new content is longer → update existing
4. If match found and same/shorter → skip
5. No match → insert as normal

## 2. Recall Improvements
- Cosine similarity threshold: 0.35 (filter irrelevant results)
- Configurable top_n, default 15
- Better system prompt formatting with importance and age

## 3. FTS5 Full-Text Search
- New FTS5 virtual table synced with memories
- Replaces LIKE queries for keyword search

## 4. Two-Pass Auto-Recall
- Pass 1: User-specific memories (by Discord user ID)
- Pass 2: Content-relevant memories (semantic + FTS5)
- Merge, dedup, cap at top_n

## Files to Modify
| File | Changes |
|------|---------|
| memory/store.go | dedup logic, FTS sync |
| memory/search.go | threshold, FTS5 query |
| agent/agent.go | two-pass recall, formatting |
| config/config.go | new config fields |
```

Všimni si struktury: **problém → řešení → konkrétní body → dotčené soubory**. Žádný kód, žádné implementační detaily -to je práce pro implementační plán.

---

## Implementační Plán

Navazuje na design dokument.

**Postup:**
1. Řekni AI aby z design docu vytvořil implementační plán
2. Plán obsahuje konkrétní kroky, pořadí, závislosti
3. Review plánu, uprav co nesedí

### Příklad: Implementační plán

Navazuje na design doc výše. Zkráceně jeden task z plánu:

```markdown
# Memory Improvements Implementation Plan

**Goal:** Fix memory recall quality and prevent duplicate storage.
**Tech Stack:** Go, SQLite FTS5

### Task 1: Add config fields for memory tuning

**Files:**
- Modify: config/config.go:52-61 (TurnConfig struct)
- Modify: config/config.go:157-177 (defaults in Load)

**Step 1:** Add three new fields to TurnConfig
(konkrétní kód s přesnými řádky)

**Step 2:** Add defaults in Load()
(konkrétní kód)

**Step 3:** Verify build
Run: go build ./...

**Step 4:** Commit
git commit -m "feat: add memory config fields"

### Task 2: Add FTS5 virtual table
...
### Task 3: Implement dedup-on-save
...
```

Všimni si rozdílu oproti design docu: **konkrétní soubory s čísly řádků, přesný kód, přesné příkazy, TDD přístup (test first), každý task končí commitem**. AI tohle dokáže implementovat task po tasku bez dalších otázek.

---

## html-communication

Na velké featury a vůbec cokoliv, co chci číst mimo terminál, mám [[Skills|skill]] `html-communication` (nahradil starší `html-plan`, po vzoru Theova skillu stejného jména). Plán, spec, findings, srovnání nebo UI mocky vygeneruje jako jeden self-contained HTML soubor a nahraje na postplan.dev, takže dostanu stabilní URL.

**Kdy se spustí:** když si řeknu o plán/spec/writeup jako HTML — nebo když prostě napíšu „HTML" na konec promptu. Ta zkratka je přímo v description skillu.

**Kdy ne:** HTML, které je součástí produktu. A běžné plánování zůstává v terminálu — samostatný dokument si zaslouží jen věc, kterou budu reálně číst a rozhodovat nad ní.

U UI mocků skill renderuje skutečné nastylované varianty označené `A`, `B`, `C` vedle sebe — odpověď pak je jen „Do C" a jede se.

---

## Plan Mode v Claude Code

Claude Code má Plan Mode - AI napíše plán a **nespustí žádný kód**.

Po dokončení plánu se zobrazí tlačítko které spustí implementaci s čistým kontextem. Tato funkce je unikátní pro Claude Code - ostatní nástroje Plan Mode sice mají, ale čistý kontext před implementací musíš řešit ručně.

**Jak ho použít:**
1. Aktivuj Plan Mode před zadáním tasku (`Shift+Tab` v Claude Code, `Tab` v OpenCode)
2. AI vypracuje plán
3. Po dokončení plánu spusť implementaci s čistým kontextem
4. AI implementuje čistě podle plánu

> Přeplněný kontext degraduje kvalitu výstupu. Čistý kontext + jasný plán = lepší kód.

---

## CLAUDE.md pro repozitář

Pro každý větší projekt nechám AI vytvořit `CLAUDE.md` přímo v repozitáři.

Tento soubor říká AI jak se má v projektu chovat: konvence, architektura, co nedělat.

AI si ho přečte automaticky při každé session.

Viz [[Prompting#CLAUDE.md|CLAUDE.md]].

---

*Viz také: [[Workflow Proces]], [[Claude Code - Tipy a Triky]], [[Prompting]]*
