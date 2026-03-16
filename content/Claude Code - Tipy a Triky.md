---
tags:
  - ai-workflow
---

# Claude Code - Tipy a Triky

Pokročilejší funkce Claude Code které používám denně.

---

## Plan Mode

Před implementací nechej AI napsat plán, bez toho aby cokoliv spustil nebo změnil.

Pak vyčisti kontext a implementuj čistě. Viz [[Plánování a Design Dokumenty#Plan Mode v Claude Code|Plan Mode]].

---

## Superpowers

Plugin který přidává **skills** (workflow šablony) přímo do Claude Code.

> Repozitář: [github.com/obra/superpowers](https://github.com/obra/superpowers), nainstalováno globálně

**Skills které používám:**

| Skill | Co dělá |
|-------|---------|
| `code-review` | Zkontroluje kód po implementaci |
| `simplify` | Zjednodušuje a čistí napsaný kód |
| `brainstorming` | Exploruje záměr a požadavky před implementací |
| `systematic-debugging` | Strukturované debugování |
| `TDD` | Test-driven development workflow |
| `writing-plans` | Pomáhá psát implementační plány |

Skills se spouštějí přirozeným jazykem nebo přes `/` v Claude Code.

---

## Parallel Agents

Claude Code umí spouštět paralelní subagenty, jeden hlavní agent rozdělí práci mezi víc subagentů.

**Pravidlo:** Subagenti jsou pro **konkrétní tasky**, ne role.
- ❌ "Buď frontend developer"
- ✅ "Implementuj login stránku"

**Jak vytvořit vlastního agenta:**
1. `/agents` → Create new agent
2. Project nebo Personal scope
3. Generate with Claude - popiš task přirozeným jazykem
4. Nastav tool permissions
5. Save
6. Zavolej přirozeným jazykem nebo přes `@NázevAgenta`

---

## MCP Servery

Rozšíření která přidávají AI nové schopnosti. Viz [[MCP Servery]].

---

## Tipy pro práci s kontextem

- Čistý kontext = lepší výstupy, neboj se začít novou session
- Velké soubory nebo dlouhé konverzace degradují kvalitu
- Plan Mode + reset kontextu je silná kombinace pro větší featury

---

## Co AI dělá automaticky

- Vytváří branche, commituje, pushuje, vytváří PR
- Opravuje testy které se rozbily
- Čte `CLAUDE.md` na začátku každé session

---

*Viz také: [[MCP Servery]], [[Plánování a Design Dokumenty]], [[Git Workflow]]*
