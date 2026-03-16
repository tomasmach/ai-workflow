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
- Rozšiřitelný přes [[MCP Servery]] a [[Claude Code - Tipy a Triky#Superpowers|Superpowers]]
- Plan mode - napíše plán, pak čistý kontext + implementace

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

## Codex (OpenAI)

Coding agent od OpenAI s GUI i TUI variantou.

**Kdy ho použít:**
- Alternativa pro GPT-4o / o3 modely
- Vlastní izolované cloudové prostředí pro běh kódu

**Osobní zkušenost:** GUI je dobré, TUI je na nic.

---

## VS Code + addony

Místo Cursoru nebo Windsurfu (přijdou mi jako bloatware) preferuji čistý VS Code s relevantními rozšířeními.

**Doporučené addony:**
- GitHub Copilot (inline suggestions)
- Claude Code extension (integrace přímo v editoru)

---

## Co nepoužívám a proč

| Nástroj | Důvod |
|---------|-------|
| Cursor | Bloatware, příliš mnoho věcí najednou |
| Windsurf | Stejný problém jako Cursor |

---

*Viz také: [[Workflow Proces]], [[Claude Code - Tipy a Triky]]*
