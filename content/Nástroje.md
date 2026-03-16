---
tags:
  - ai-workflow
---

# Nástroje

Přehled nástrojů, které používám pro AI-driven development.

---

## Claude Code

Primární nástroj. Terminálový AI coding agent od Anthropic, běží přímo v terminálu a pracuje s celým repozitářem.

Vždy spouštím s `--dangerously-skip-permissions`, ať nemusím každou chvíli potvrzovat povolení pro každý příkaz.

**Proč Claude Code:**
- Nejlepší pochopení kontextu celého projektu
- Nativní integrace s gitem (branche, commity, PR)
- Rozšiřitelný přes [[MCP Servery]] a [[Claude Code - Tipy a Triky#Superpowers|Superpowers]]
- Plan mode - napíše plán, pak čistý kontext + implementace

---

## OpenCode

TUI (terminal UI) alternativa, která agreguje více AI modelů na jednom místě.

**Proč OpenCode:**
- Jedno TUI pro všechny zaplacené subscripce (Claude, GPT, Gemini...)
- Lze spustit jako server, připojíš se z libovolného počítače na stejné síti
- Nejlépe poskládané UI ze všech terminal agentů
- Ideální pokud nechceš být locked-in na jeden model
- Doporučuju jako default pokud nepoužíváš Anthropic ekosystém

> Repozitář: [opencode.ai](https://opencode.ai)

**Pozor na vendor lock u Anthropic:** Anthropic subscription (Pro/Max plan) se dá oficiálně použít pouze v Claude Code a Claude GUI/TUI. Claude Code se dá po ohýbání rozchodit i s jinými modely, ale subscription samotný je locked-in. Do OpenCode se dá přihlásit přes Anthropic OAuth, ale riskuješ tím ban účtu. Nestává se to často, ale stává se. Pokud chceš flexibilitu, jdi do OpenCode.

---

## Codex (OpenAI)

Cloudový coding agent od OpenAI s vlastní GUI i TUI aplikací.

**Kdy ho použít:**
- Alternativa pro GPT-5.4 / GPT-5.3-Codex modely
- Vlastní izolované cloudové prostředí pro běh kódu

---

## VS Code + addony

Místo Cursoru nebo Windsurfu (přijdou mi jako bloatware) preferuji čistý VS Code s relevantními rozšířeními.

**Doporučené addony:**
- Codex extension (inline suggestions)
- Claude Code extension (integrace přímo v editoru)

---

## Co nepoužívám a proč

| Nástroj | Důvod |
|---------|-------|
| Cursor | Bloatware, příliš mnoho věcí najednou |
| Windsurf | Stejný problém jako Cursor |

---

*Viz také: [[Workflow Proces]], [[Claude Code - Tipy a Triky]]*
