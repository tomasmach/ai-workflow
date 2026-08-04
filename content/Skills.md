---
tags:
  - ai-workflow
---

# Skills

Skills jsou dnes hlavní způsob, jak si Claude Code rozšiřuji. Nahradily mi to, na co jsem dřív používal pluginy s hotovými sadami workflow šablon.

---

## Co to je

Skill je adresář se souborem `SKILL.md`, který obsahuje instrukce pro konkrétní typ práce. Frontmatter popisuje, **kdy** se má skill použít; tělo popisuje **jak** tu práci odvést.

```
~/.claude/skills/
  copywriting/
    SKILL.md
  codex-review/
    SKILL.md
```

Claude si podle popisu sám vybere relevantní skill, nebo ho spustíš explicitně přes `/nazev-skillu`.

---

## Skill vs. plugin vs. MCP

Tři vrstvy rozšíření, které se pletou:

| Vrstva | Co přidává | Kde žije |
|--------|-----------|----------|
| **Skill** | Instrukce — jak dělat určitý typ práce | `~/.claude/skills/` |
| **Plugin** | Balík skills, agentů, commandů a MCP serverů | `~/.claude/plugins/`, viz [[Pluginy a Rozšíření]] |
| **MCP server** | Nové *nástroje* — přístup k API, databázi, browseru | Konfigurace, viz [[MCP Servery]] |

Zkratka: skill mění **chování**, MCP přidává **schopnosti**, plugin je **distribuční obal** pro obojí.

---

## Moje kategorie

Mám globálně asi 60 skills. Nejsou to všechno moje autorské věci — část jsou instalované sady, které jsem si nechal.

### Codex

| Skill | K čemu |
|-------|--------|
| `codex-implementation` | Předání implementačního tasku na gpt-5.6-sol |
| `codex-review` | Review diffu, branche nebo commitu |
| `codex-computer-use` | Ověření běžící aplikace, screenshoty |

Viz [[Codex CLI]].

### Workflow

| Skill | K čemu |
|-------|--------|
| `html-plan` | Interaktivní HTML plán pro velké featury |
| `verify` | Ověření změny v reálné běžící aplikaci, ne jen v testech |
| `full-output-enforcement` | Zákaz zkracování a placeholderů ve výstupu |
| `humanizer` | Odstranění znaků AI psaní z textu |

### Obsidian a znalosti

| Skill | K čemu |
|-------|--------|
| `obsidian-cli` | Práce s vaultem přes CLI — čtení, zápis, hledání |
| `summarize` | Shrnutí videa, článku, PDF do vault noty s wikilinky |
| `summarize-call` | Přepis hovoru s diarizací + noty účastníků |

### Design a frontend

`design-taste-frontend`, `high-end-visual-design`, `redesign-existing-projects`, `image-to-code`, `minimalist-ui`, `industrial-brutalist-ui`, `brandkit`, `gpt-taste`, `stitch-design-taste`, `imagegen-frontend-web`, `imagegen-frontend-mobile`

Anti-slop sada — brání tomu, aby výstup vypadal jako generický AI template.

### Marketing a growth

Největší skupina — copywriting, CRO, SEO, ads, e-maily, pricing, analytics, ASO, PR a další. Používám je nárazově, ale když je potřeba, ušetří spoustu promptování.

---

## Jak si napsat vlastní

1. Vytvoř `~/.claude/skills/nazev/SKILL.md`
2. Do frontmatteru dej `name` a `description` — description rozhoduje, jestli si skill Claude vybere, takže do něj patří konkrétní spouštěcí fráze
3. Do těla napiš postup

**Nejčastější chyba:** vágní `description`. Skill se pak nikdy nespustí sám a musíš ho volat ručně.

---

## Skope

- **Globální** (`~/.claude/skills/`) — napříč všemi projekty
- **Projektové** (`.claude/skills/` v repu) — jen pro daný projekt, commitne se do gitu a dostane ho každý, kdo repo naklonuje

Stejná logika jako u [[Prompting#Repozitářový CLAUDE.md|CLAUDE.md]].

---

*Viz také: [[Claude Code - Tipy a Triky]], [[Pluginy a Rozšíření]], [[Codex CLI]]*
