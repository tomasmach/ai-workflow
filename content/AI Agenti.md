---
tags:
  - ai-workflow
---

# AI Agenti - Přehled a Doporučení

Moje osobní zkušenosti s AI agenty, subscripcemi a co se vyplatí.

---

## Můj primární stack

**Anthropic / Claude** je za mě nejlepší pro programování. Nejvíc mi sedí, nejspokojenější jsem s ním.

Modely které používám:
- **Sonnet 4.6** - 90 % práce. Naprostá většina tasků, implementace, debugging, refactoring.
- **Opus 4.6** - jen na nejtěžší tasky a velké plánování. Žere víc tokenů, ale kde na tom záleží, stojí to za to.
- **Haiku 4.5** - triviální tasky v rámci parallel agents (jednoduché čtení souborů, basic search, jednořádkové edity). Šetří tokeny tam kde Sonnet by byl overkill.

**Strategie Opus + Sonnet subagenti:**
Opus naplánuje a vyvolá paralelní subagenty → subagenti (Sonnet) implementují → Opus zkontroluje výsledky. Ušetří tokeny a zároveň využiješ silný model tam kde to má smysl.

Viz [[Plánování a Design Dokumenty]] a [[Claude Code - Tipy a Triky#Parallel Agents|Parallel Agents]].

---

## Anthropic subscripce

| Plán | Cena | Doporučení |
|------|------|------------|
| Pro | $20/měs | ❌ Nevyplatí se, limity jsou příliš nízké pro reálný development |
| Max | $100/měs | ✅ Doporučuji, vystačí na denní coding workflow |
| Max | $200/měs | Pokud ti $100 nestačí |

**Závěr:** Anthropic Pro ($20) nemá pro coding moc smysl. Připlať si nebo zvol jinou alternativu.

---

## Alternativy - pokud chceš ušetřit

### OpenAI Codex
- Dobrá alternativa za $20
- ⚠️ Poslední dobou zužuje limity, sleduj situaci

### Kimi 2.5
- $20/měs, překvapivě dobrý výkon
- Vhodná alternativa do $20 budgetu

### Z.ai
- Neskutečně velké limity
- Kód není na úrovni Claude, ale **cena/výkon** je zajímavá pro méně náročné tasky

### MiniMax 2.5
- Prý dobrý poměr cena/výkon, osobně jsem nevyzkoušel

### OpenCode Zen / Go
- Subscripce přímo v OpenCode, umožní ti používat více modelů v jednom TUI
- Viz [[Nástroje#OpenCode|OpenCode]]

---

## Co nedoporučuji

**API klíče + OpenRouter** - na první pohled flexibilní, v praxi drahé. Při reálném workloadu zaplatíš výrazně víc než za předplacenou subscripci.

---

## Důležitý mindset

> Buď připravený kdykoliv přejít k něčemu jinýmu.

Svět AI se hýbe extrémně rychle. Dnes nejlepší agent nemusí být nejlepší za půl roku. Netlp na jednom nástroji, sleduj co se děje a neváhej experimentovat.

---

*Viz také: [[Nástroje]], [[Claude Code - Tipy a Triky]]*
