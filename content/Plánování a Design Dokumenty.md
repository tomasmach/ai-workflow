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

Používám na to skill `brainstorming` ze [[Pluginy a Rozšíření#Superpowers|Superpowers]]. Ten exploruje záměr, požadavky a design předtím než se začne cokoliv implementovat.

**Postup:**
1. Spusť `brainstorming` skill
2. AI klade otázky, ty odpovídáš
3. Iteruj dokud nemáš jasno
4. Výsledek uložíš jako design doc

Cíl: mít jasno v tom **co** buduješ předtím, než se začne psát kód.

---

## Implementační Plán

Navazuje na design dokument. Superpowers ho vytvoří automaticky po dokončení design docu, nemusíš nic extra zadávat.

Plán obsahuje konkrétní kroky, pořadí a závislosti. Projdi ho a uprav co nesedí.

---

## Plan Mode v Claude Code

Claude Code má Plan Mode - AI napíše plán a **nespustí žádný kód**.

Po dokončení plánu se zobrazí tlačítko které spustí implementaci s čistým kontextem. Plan Mode mají i ostatní nástroje (OpenCode, Codex...), ale funkce "Clear context and execute plan" je unikátní pro Claude Code. Jinde musíš čistý kontext před implementací řešit ručně.

**Jak ho použít:**
1. Aktivuj Plan Mode před zadáním tasku
2. AI vypracuje plán
3. Klikni na tlačítko pro spuštění - Claude Code sám začne s čistým kontextem
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
