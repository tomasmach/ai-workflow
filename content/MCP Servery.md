---
tags:
  - ai-workflow
---

# MCP Servery

## Co jsou MCP Servery

**MCP (Model Context Protocol)** je otevřený standard který umožňuje AI agentům se připojit k externím nástrojům, službám a datovým zdrojům.

Zjednodušeně: MCP server je plugin který dá AI agentovi nové schopnosti, například přístup k databázi, browseru, GitHub API, nebo externím dokumentům.

Funguje jako most mezi AI a světem mimo konverzaci.

> MCP server je jako USB adaptér, umožní ti připojit cokoliv k čemukoliv.

---

## Jak fungují

1. MCP server běží lokálně nebo vzdáleně
2. AI agent se k němu připojí
3. Agent může volat jeho funkce jako by byly jeho vlastní nástroje
4. Výsledky dostane zpět do kontextu

---

## Servery které používám

### Vývojářské

| Server | K čemu |
|--------|--------|
| **Context7** | Up-to-date dokumentace knihoven |
| **Playwright** | Browser automation, AI může ovládat prohlížeč |
| **Supabase** | Přímé databázové operace |
| **Vercel** | Deploy, env proměnné, logy |
| **GitHub** | Čtení/zápis repozitářů, issues, PR |
| **Pencil** | Editor `.pen` designových souborů |

Většina z nich přichází s pluginem, ne jako samostatná instalace. Viz [[Pluginy a Rozšíření]].

### Osobní / connectory

| Server | K čemu |
|--------|--------|
| **Gmail** | Čtení vláken, drafty, štítky |
| **Google Calendar** | Správa kalendáře |
| **Google Drive** | Čtení dokumentů |
| **Slack** | Čtení a psaní zpráv |
| **Linear** | Issues a projekty |

Connectory se autorizují přes OAuth v nastavení claude.ai. V headless nebo cron běhu nemusí být dostupné — počítej s tím u automatizací.

---

## Context7 - nejdůležitější

Řeší jeden z největších problémů AI coding agentů: **zastaralé znalosti**.

AI byl natrénovaný k určitému datu, nezná nové verze knihoven, API změny, nové funkce.

Context7 při každém promptu stáhne aktuální dokumentaci a dá ji AI do kontextu.

**Výsledek:** AI píše kód podle aktuální verze knihovny, ne té co znal při tréninku.

Používej ho i u knihoven, které AI „zjevně zná" — React, Next.js, Tailwind. Právě u nich je největší šance, že si model pamatuje starší API.

---

## Kdy MCP a kdy skill

Tohle se plete. MCP server přidává **nástroj** — schopnost něco udělat, co jinak nejde. Skill přidává **instrukce** — jak něco dělat dobře.

Praktický příklad: pro Obsidian jsem MCP server opustil ve prospěch skillu `obsidian-cli`, který jen volá existující CLI. Když nástroj v systému už je, MCP vrstva navíc jen ubírá kontext.

Viz [[Skills#Skill vs. plugin vs. MCP|srovnání vrstev]].

---

## Kde najít MCP servery

- `/plugin` v Claude Code — oficiální marketplace
- GitHub - hledej `mcp-server-*`
- Komunity kolem jednotlivých nástrojů (Supabase, Linear, Notion...)

---

*Viz také: [[Claude Code - Tipy a Triky]], [[Skills]], [[Pluginy a Rozšíření]]*
