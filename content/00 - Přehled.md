---
tags:
  - ai-workflow
---

# AI Programming Workflow

Můj osobní přístup k AI-driven developmentu. Vše co používám, jak to používám a proč.

---

## Obsah

**Základ**
- [[Nástroje]] - Claude Code, Codex, OpenCode, VS Code
- [[Výběr Modelu]] - který model na jaký task
- [[Workflow Proces]] - jak vypadá typická práce od nápadu po merge

**Nástroje do hloubky**
- [[Codex CLI]] - gpt-5.6-sol na backend, investigaci a bulk práci
- [[Claude Code - Tipy a Triky]] - Plan Mode, parallel agents, workflows
- [[Skills]] - hlavní způsob rozšíření Claude Code
- [[Pluginy a Rozšíření]] - co mám zapnuté a co jsem opustil
- [[MCP Servery]] - co jsou MCP, Context7, Playwright...

**Konfigurace**
- [[Globální CLAUDE.md]] - můj globální konfigurační soubor
- [[Prompting]] - jak psát prompty, CLAUDE.md a AGENTS.md
- [[Memory a Hooks]] - persistent memory, hooks, settings.json
- [[Context Management]] - jak efektivně pracovat s kontextem AI

**Proces**
- [[Plánování a Design Dokumenty]] - design docy, implementační plány, Plan Mode
- [[Git Workflow]] - branche, commity, PR, vše řídí AI
- [[Onboarding Nového Projektu]] - jak připravit nový projekt
- [[AI Agenti]] - přehled agentů, subscripce, zkušenosti

---

## TL;DR

> Já řeším **co** a **proč**. AI řeší **jak**.

1. Malá featura → rovnou prompt → AI implementuje
2. Velká featura → design doc → implementační plán → AI implementuje
3. Backend a investigaci deleguj na [[Codex CLI|Codex]], UI a rozhodování nech na Claude
4. AI vždy commituje, pushuje, vytváří PR
5. Po implementaci: `/code-review` → `/simplify` → Commit

---

## Nástroje na první pohled

| Nástroj | Role |
|---------|------|
| [[Nástroje#Claude Code\|Claude Code]] | Primární agent — orchestrace, UI, rozhodování |
| [[Codex CLI]] | Backend implementace, čtení kódu, investigace |
| [[Nástroje#OpenCode\|OpenCode]] | Multi-model TUI, server mode |
| VS Code | Editor (bez Cursoru/Windsurfu) |

---

## Přehled modelů

| Model | Kdy |
|-------|-----|
| gpt-5.6-sol | Backend, investigace, bulk práce — přes [[Codex CLI]] |
| fable-5 | Taste calls — UI, copy, tvar API. Review |
| opus-4.8 | Náročné tasky, plánování, review |
| sonnet-5 | Běžná práce a tenké wrappery |
| ~~Haiku~~ | Nepoužívám, bez výjimek |

Podrobná pravidla v [[Výběr Modelu]].
