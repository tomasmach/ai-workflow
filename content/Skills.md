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

Mám globálně ~26 skills (v Claude i Codexu). V srpnu 2026 jsem jich 36 promazal — hlavně celý marketing balík (copywriting, CRO, SEO, ads, e-maily, pricing…). Používal jsem je nárazově, ale každý skill má description, který sedí v kontextu **každé session**, takže za nepoužívané skills platíš pořád. Archiv leží vedle skills složky, kdyby něco chybělo.

### Vlastní workflow skilly

Dva nejdůležitější, psané podle vzoru z [Theova videa](https://www.youtube.com/watch?v=e1snsuY4lTI) — description je sada spouštěcích frází, ne popis:

| Skill | K čemu |
|-------|--------|
| `file-pr` | Worktree lifecycle: hotová větev → draft PR s důkazem → „otevři PR" → úklid po merge. Viz [[Git Workflow]] |
| `html-communication` | Plán, spec, findings nebo UI mocky jako HTML, hostované přes postplan.dev. Stačí napsat „HTML" na konec promptu. Nahradil starší `html-plan` |

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
| `verify` | Ověření změny v reálné běžící aplikaci, ne jen v testech |
| `full-output-enforcement` | Zákaz zkracování a placeholderů ve výstupu |
| `humanizer` | Odstranění znaků AI psaní z textu. Od přepisu [[Globální CLAUDE.md]] ho agent pouští sám na každý text pro lidi |
| `bro` | Vysvětlení srozumitelně, bez žargonu |

### Obsidian a znalosti

| Skill | K čemu |
|-------|--------|
| `obsidian-cli` | Práce s vaultem přes CLI — čtení, zápis, hledání |
| `summarize` | Shrnutí videa, článku, PDF do vault noty s wikilinky |
| `summarize-call` | Přepis hovoru s diarizací + noty účastníků |

### Design a frontend

`design-taste-frontend`, `high-end-visual-design`, `redesign-existing-projects`, `image-to-code`, `minimalist-ui`, `industrial-brutalist-ui`, `brandkit`, `gpt-taste`, `stitch-design-taste`, `imagegen-frontend-web`, `imagegen-frontend-mobile`, `aso`

Anti-slop sada — brání tomu, aby výstup vypadal jako generický AI template. `aso` zůstal z marketing balíku, protože App Store listingy jsou moje denní práce (Uprate, Na Pivo).

---

## Jak si napsat vlastní

1. Vytvoř `~/.claude/skills/nazev/SKILL.md`
2. Do frontmatteru dej `name` a `description` — description rozhoduje, jestli si skill Claude vybere, takže do něj patří konkrétní spouštěcí fráze
3. Do těla napiš postup

**Nejčastější chyba:** vágní `description`. Skill se pak nikdy nespustí sám a musíš ho volat ručně.

**Druhá nejčastější chyba (Theova lekce):** description jako popis toho, co skill dělá. Description je v kontextu vždycky, i když se skill nepoužije — takže má obsahovat **kdy ho spustit** (trigger fráze), ne **co umí**. „Use when the user asks to file, open, or create a PR" porazí odstavec o tom, jak skill funguje. Extrém, který funguje: `html-communication` má v description i „or if they mention 'HTML' with no additional context" — stačí napsat „HTML" na konec promptu.

---

## Skope

- **Globální** (`~/.claude/skills/`) — napříč všemi projekty
- **Projektové** (`.claude/skills/` v repu) — jen pro daný projekt, commitne se do gitu a dostane ho každý, kdo repo naklonuje

Stejná logika jako u [[Prompting#Repozitářový CLAUDE.md|CLAUDE.md]].

---

*Viz také: [[Claude Code - Tipy a Triky]], [[Pluginy a Rozšíření]], [[Codex CLI]]*
