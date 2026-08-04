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

## Skills

Hlavní způsob, jak si Claude Code rozšiřuji — instrukce pro konkrétní typ práce, které si AI samo vybere podle popisu. Mám jich globálně kolem šedesáti.

Podrobně viz [[Skills]].

---

## Parallel Agents

Claude Code umí spouštět paralelní subagenty, jeden hlavní agent rozdělí práci mezi víc subagentů.

**Pravidlo:** Subagenti jsou pro **konkrétní tasky**, ne role.
- ❌ "Buď frontend developer"
- ✅ "Implementuj login stránku"

**Kdy je nasadit:** 2+ nezávislých tasků bez sdíleného stavu. Každý subagent má vlastní kontext, takže se neplýtvá opakováním kontextu mezi sekvenčními kroky.

**Volba modelu** pro subagenty je samostatná disciplína, viz [[Výběr Modelu]]. Zkráceně: backend a investigace přes [[Codex CLI|Codex]], taste calls přes fable-5 nebo opus-4.8, nikdy Haiku.

**Jak vytvořit vlastního agenta:**
1. `/agents` → Create new agent
2. Project nebo Personal scope
3. Generate with Claude - popiš task přirozeným jazykem
4. Nastav tool permissions
5. Save
6. Zavolej přirozeným jazykem nebo přes `@NázevAgenta`

---

## Workflows

Když potřebuješ orchestraci, která má být **deterministická** — smyčky, podmínky, fan-out přes desítky agentů — nestačí slíbit to promptem. Workflow je skript, který strukturu vynutí.

Typické tvary:

| Tvar | K čemu |
|------|--------|
| pipeline | Každá položka projde všemi fázemi nezávisle, bez čekání na ostatní |
| parallel | Bariéra — počká na všechny, teprve pak pokračuje |
| adversarial verify | Nález ověří několik nezávislých skeptiků, přežije jen většinový |
| loop-until-dry | Hledej, dokud N kol po sobě nepřinese nic nového |

**Default je pipeline.** Bariéra je namístě jen tehdy, když další fáze skutečně potřebuje výsledky *všech* předchozích najednou — třeba deduplikace napříč nálezy.

Workflows umí spustit desítky agentů, takže je nepouštím implicitně — jen když si o to řeknu.

---

## Slash commandy

Zabudované, které používám nejvíc:

| Příkaz | Co dělá |
|--------|---------|
| `/code-review` | Review pracovního diffu |
| `/simplify` | Zjednodušení právě napsaného kódu |
| `/init` | Vygeneruje `CLAUDE.md` pro repozitář |
| `/agents` | Správa subagentů |
| `/plugin` | Správa pluginů |
| `/config` | Nastavení |

---

## MCP Servery

Rozšíření která přidávají AI nové *nástroje*. Viz [[MCP Servery]].

---

## Tipy pro práci s kontextem

- Čistý kontext = lepší výstupy, neboj se začít novou session
- Velké soubory nebo dlouhé konverzace degradují kvalitu
- Plan Mode + reset kontextu je silná kombinace pro větší featury
- Čtení souborů a logů deleguj na [[Codex CLI|Codex]] — drží raw obsah mimo Claude kontext

Podrobně viz [[Context Management]].

---

## Co AI dělá automaticky

- Vytváří branche, commituje, pushuje, vytváří PR
- Opravuje testy které se rozbily — i ty, které s taskem nesouvisí
- Čte `CLAUDE.md` na začátku každé session
- Ukládá si poznatky do [[Memory a Hooks|persistent memory]]

---

*Viz také: [[Skills]], [[MCP Servery]], [[Plánování a Design Dokumenty]], [[Git Workflow]]*
