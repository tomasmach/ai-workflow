---
tags:
  - ai-workflow
---

# AI Programming Workflow

Můj osobní přístup k AI-driven developmentu. Vše co používám, jak to používám a proč.

---

## Obsah

- [[Nástroje]] - Claude Code, OpenCode, Codex, VS Code
- [[Workflow Proces]] - jak vypadá typická práce od nápadu po merge
- [[Plánování a Design Dokumenty]] - design docy, implementační plány, Plan Mode
- [[Claude Code - Tipy a Triky]] - Superpowers, parallel agents, správa kontextu
- [[MCP Servery]] - co jsou MCP, Context7, GitHub, Playwright...
- [[Git Workflow]] - branche, commity, PR, vše řídí AI
- [[Prompting]] - jak psát prompty, CLAUDE.md konfigurace
- [[AI Agenti]] - přehled agentů, doporučené subscripce, zkušenosti
- [[Pluginy a Rozšíření]] - doporučené pluginy pro Claude Code
- [[Globální CLAUDE.md]] - můj globální konfigurační soubor
- [[Context Management]] - jak efektivně pracovat s kontextem AI
- [[Onboarding Nového Projektu]] - jak připravit nový projekt pro AI-driven development

---

## TL;DR

> Já řeším **co** a **proč**. AI řeší **jak**.

1. Malá featura → rovnou prompt → AI implementuje
2. Velká featura → design doc → implementační plán → AI implementuje
3. AI vždy commituje, pushuje, vytváří PR
4. Po implementaci: Code Review (Superpowers) → Simplify → Commit

---

## Nástroje na první pohled

| Nástroj | Role |
|---------|------|
| [[Nástroje#Claude Code\|Claude Code]] | Primární coding agent |
| [[Nástroje#OpenCode\|OpenCode]] | Multi-model TUI, server mode |
| [[Nástroje#Codex (OpenAI)\|Codex]] | Alternativa na OpenAI modely |
| VS Code | Editor (bez Cursoru/Windsurfu) |

---

## Přehled modelů

| Model | Kdy |
|-------|-----|
| Sonnet 4.6 | 90 % práce - implementace, debugging, refactoring |
| Opus 4.6 | Nejtěžší tasky, velké plánování |
| Haiku 4.5 | Triviální tasky v rámci parallel agents |

Viz [[AI Agenti]] pro detaily o subscripcích.
