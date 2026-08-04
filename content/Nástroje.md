---
tags:
  - ai-workflow
---

# Nástroje

Přehled nástrojů, které používám pro AI-driven development.

---

## Claude Code

Primární nástroj. Terminálový AI coding agent od Anthropic, běží přímo v terminálu a pracuje s celým repozitářem.

**Proč Claude Code:**
- Nejlepší pochopení kontextu celého projektu
- Nativní integrace s gitem (branche, commity, PR)
- Rozšiřitelný přes [[Skills]], [[Pluginy a Rozšíření|pluginy]] a [[MCP Servery]]
- Plan mode - napíše plán, pak čistý kontext + implementace
- Orchestrace subagentů a [[Claude Code - Tipy a Triky#Workflows|workflows]]

Dostupný je i mimo terminál — desktop aplikace, web, rozšíření do VS Code a JetBrains. Držím se terminálu.

---

## Codex CLI

Coding agent od OpenAI, jediná cesta k modelu **gpt-5.6-sol**.

Dnes na něm stojí veškerá backendová implementace, čtení kódu a investigace. Není to alternativa ke Claude Code, ale jeho doplněk — Claude orchestruje, Codex odvádí objemnou práci.

Podrobně viz [[Codex CLI]].

**Změna názoru:** dřív jsem psal, že GUI je dobré a TUI k ničemu. S gpt-5.6-sol se to obrátilo — `codex exec` volaný z Claude Code je dnes ta forma, kterou používám nejvíc.

---

## OpenCode

TUI (terminal UI) pro AI-driven development. Není to agent sám o sobě - je to rozhraní přes které se připojíš k prakticky jakémukoliv AI poskytovateli (Anthropic, OpenAI, Google, Mistral...). Za mě **nejlepší TUI** co existuje.

**Proč OpenCode:**
- Připojíš si vlastní subscripce od různých AI firem, všechno na jednom místě
- Lze spustit jako server, připojíš se z libovolného počítače na stejné síti
- Nejlépe poskládané UI ze všech terminálových nástrojů
- Ideální pokud nechceš být locked-in na jednoho poskytovatele

> Repozitář: [opencode.ai](https://opencode.ai)

---

## VS Code + addony

Místo Cursoru nebo Windsurfu (přijdou mi jako bloatware) preferuji čistý VS Code s relevantními rozšířeními.

**Doporučené addony:**
- GitHub Copilot (inline suggestions)
- Claude Code extension (integrace přímo v editoru)

---

## vite-plus toolchain

Node, npm, npx, corepack i `codex` u mě běží přes `~/.vite-plus`. Symlink `current` ukazuje na aktivní verzi.

**Pozor při úklidu:** než smažeš „starou" verzi, rozřeš, kam `current` ukazuje. Jinak si odstřelíš aktivní toolchain včetně Codexu.

---

## Co nepoužívám a proč

| Nástroj | Důvod |
|---------|-------|
| Cursor | Bloatware, příliš mnoho věcí najednou |
| Windsurf | Stejný problém jako Cursor |

---

*Viz také: [[Codex CLI]], [[Workflow Proces]], [[Claude Code - Tipy a Triky]]*
