---
tags:
  - ai-workflow
---

# Pluginy a Rozšíření

Pluginy pro Claude Code, které reálně používám.

Plugin je distribuční obal — může přinést skills, agenty, slash commandy i MCP servery najednou. Instalují se z marketplace přes `/plugin`. Rozdíl oproti ostatním vrstvám rozšíření viz [[Skills#Skill vs. plugin vs. MCP|skill vs. plugin vs. MCP]].

---

## Co mám zapnuté

| Plugin | Co přidává |
|--------|-----------|
| **codex** | `codex:rescue` agent a setup pro [[Codex CLI]] — druhý nezávislý průchod, když se Claude zasekne |
| **context7** | MCP server s aktuální dokumentací knihoven, viz [[MCP Servery#Context7 - nejdůležitější\|Context7]] |
| **playwright** | Browser automation — ovládání prohlížeče, testování webových UI |
| **github** | Práce s repozitáři, issues a PR |
| **supabase** | Databázové operace |
| **vercel** | Deploy, env proměnné, specializovaní agenti na Next.js a AI SDK |
| **ui-ux-pro-max** | Knihovna designových stylů, palet, font pairů a UX pravidel |

---

## Zabudované nahradilo pluginy

Claude Code má dnes nativně to, na co jsem dřív potřeboval plugin:

| Příkaz | Co dělá |
|--------|---------|
| `/code-review` | Review pracovního diffu |
| `/simplify` | Zjednodušení právě napsaného kódu — reuse, čitelnost, odstranění komplexity |
| `/security-review` | Bezpečnostní kontrola |
| `/review` | Review GitHub PR |

Proto mám `code-simplifier` i samostatný `code-review` plugin **vypnuté** — dělaly totéž a žraly víc tokenů.

---

## Co jsem opustil

**Superpowers.** Dlouho to byl můj hlavní plugin — kolekce workflow skills (`brainstorming`, `systematic-debugging`, `writing-plans`, `TDD`, `code-review`). Dnes ho nepoužívám vůbec. Zabudované příkazy pokrývají review a simplify, na plánování mám vlastní [[Skills|skill]] `html-plan` a zbytek jsem nahradil vlastními skills, které sedí přesně na moji práci.

**Samostatný Code Review plugin** — příliš mnoho tokenů oproti zabudovanému `/code-review`.

---

## Zapnutí a vypnutí

Plugin nemusíš odinstalovávat, stačí ho vypnout v `~/.claude/settings.json`:

```json
"enabledPlugins": {
  "context7@claude-plugins-official": true,
  "code-simplifier@claude-plugins-official": false
}
```

Viz [[Memory a Hooks#Další nastavení v settings.json|settings.json]].

---

## Pořadí po implementaci

```
Implementace → /code-review → /simplify → Commit
```

---

*Viz také: [[Skills]], [[MCP Servery]], [[Workflow Proces]]*
