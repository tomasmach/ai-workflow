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

| Server | K čemu |
|--------|--------|
| **Context7** | Up-to-date dokumentace knihoven |
| **GitHub** | Čtení/zápis repozitářů, issues, PR přímo z AI |
| **Playwright** | Browser automation, AI může ovládat prohlížeč |
| **Supabase** | Přímé databázové operace |
| **Obsidian** | Čtení a zápis do Obsidian vault |
| **Google Calendar** | Správa kalendáře |

---

## Context7 - nejdůležitější

Řeší jeden z největších problémů AI coding agentů: **zastaralé znalosti**.

AI byl natrénovaný k určitému datu, nezná nové verze knihoven, API změny, nové funkce.

Context7 při každém promptu stáhne aktuální dokumentaci a dá ji AI do kontextu.

**Výsledek:** AI píše kód podle aktuální verze knihovny, ne té co znal při tréninku.

---

## MCP servery žerou kontext

I když MCP server právě nepoužíváš, jeho definice a tool descriptions zabírají místo v kontextu. Čím víc serverů máš zapnutých, tím míň kontextu zbývá pro tvou práci. Ideální je vypínat servery které zrovna nepotřebuješ.

---

## Kde najít MCP servery

- GitHub - hledej `mcp-server-*`
- Komunity kolem jednotlivých nástrojů (Supabase, Linear, Notion...)

---

*Viz také: [[Claude Code - Tipy a Triky]], [[Nástroje]]*
