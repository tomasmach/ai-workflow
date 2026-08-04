---
tags:
  - ai-workflow
---

# Codex CLI

Coding agent od OpenAI. Jediná cesta k modelu **gpt-5.6-sol**, který mi dnes dělá většinu backendové a průzkumné práce.

> Instalace: `codex` CLI, u mě přes [[Nástroje#vite-plus toolchain|~/.vite-plus]]

---

## Kdy Codex místo Claude

**Backend implementace** — route handlery, databáze a schema, server logika, skripty, migrace, zpracování dat, CLI nástroje. Cokoliv bez uživatelského rozhraní jde defaultně přes `codex exec`, i drobnosti.

**Čtení a investigace** — čtení kódu, grepování logů, trasování bugu, průzkum neznámého repozitáře. `codex exec -s read-only`. Je to levné a hlavně to drží raw obsah souborů a logů mimo Claude kontext.

**Bulk práce** — jasně zadaná implementace, analýza dat. S `low` reasoning effortem.

**Computer use** — spuštění aplikace, ověření UI flow, screenshoty, simulátory, nezávislá kontrola běžící aplikace.

Naopak **taste calls** (UI, copy, tvar veřejného API) Codexu nepatří — na to viz [[Výběr Modelu#Rozdělení rolí u UI|rozdělení rolí]].

---

## Reasoning effort

Volí se per run, ne v configu:

```bash
codex exec -c model_reasoning_effort="low" "..."
```

| Level | Kdy |
|-------|-----|
| `low` | Mechanická práce, jasná specifikace. Sol je silný i tady |
| `medium` | Default pro běžnou práci |
| `high` | Jen skutečně těžké problémy |

Nikdy nejdi nad `high`. Flag posílej vždy explicitně — spoléhat na default v configu je zdroj překvapení.

---

## Globální AGENTS.md

Codex čte `~/.codex/AGENTS.md`, což je jeho ekvivalent [[Globální CLAUDE.md]].

**Obsah držím synchronizovaný s CLAUDE.md.** Když backend a investigace jdou defaultně přes Codex, pravidlo které je jen v CLAUDE.md platí fakticky pro polovinu mé práce. Viz [[Prompting#agents.md - ostatní nástroje|AGENTS.md]].

---

## Volání Codexu z Claude Code

Claude Code má na to sadu skills, viz [[Skills]]:

| Skill | K čemu |
|-------|--------|
| `codex-implementation` | Předání implementačního tasku |
| `codex-review` | Review necommitnutých změn, branch diffu nebo commitu |
| `codex-computer-use` | Ověření běžící aplikace, screenshoty, browser automation |

Kromě toho je nainstalovaný oficiální **codex plugin** (`codex@openai-codex`) s `codex:rescue` agentem — na situace, kdy se Claude zasekne nebo chci druhý nezávislý diagnostický průchod.

---

## Codex uvnitř workflows a subagentů

`model` parametr v Agent/Workflow bere jen Claude modely. Obchází se to tenkým wrapperem:

1. Spusť Claude agenta s `model: 'sonnet'`, `effort: 'low'`
2. Jeho prompt mu řekne, ať sestaví samostatný codex prompt, pustí `codex exec` přes Bash a vrátí surový výstup **doslova**
3. Wrapper sám nic nevymýšlí — jen přenáší prompt tam a odpověď zpět

Na co si dát pozor:

- Wrapper musí dostat **všechno v promptu** — Codex nevidí kontext workflow
- Musí selhat hlasitě (vrátit chybu), ne potichu nahradit vlastní odpovědí
- Labeluj je prefixem `gpt-5.6-sol:` — UI ukazuje Claude model wrapperu, label je jediná stopa po skutečném workeru
- Codex běhy přesahují 10minutový Bash timeout → explicitní timeout nebo běh na pozadí
- Paralelní implementační agenti potřebují `isolation: 'worktree'`, jinak si edity kolidují
- Token budget workflow počítá jen Claude tokeny — Codex práce je v něm neviditelná

---

## Osobní zkušenost

Dřív jsem Codex odepisoval — GUI dobré, TUI k ničemu. To se změnilo s gpt-5.6-sol: dnes je to pracovní kůň na backend a investigaci a Claude si šetřím na orchestraci, UI a rozhodování.

---

*Viz také: [[Výběr Modelu]], [[Nástroje]], [[Skills]], [[Globální CLAUDE.md]]*
