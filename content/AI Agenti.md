---
tags:
  - ai-workflow
---

# AI Agenti - Přehled a Doporučení

Moje osobní zkušenosti s AI agenty, subscripcemi a co se vyplatí.

---

## Můj primární stack

Dnes je to **dvojice**, ne jeden nástroj:

- **Claude Code** (Anthropic) — orchestrace, UI práce, rozhodování, práce, kde záleží na taste
- **Codex CLI** (OpenAI, model gpt-5.6-sol) — backend implementace, čtení kódu, investigace, bulk práce

Claude drží kontext a rozhoduje, Codex odvádí objemnou práci a drží raw soubory mimo Claude kontext. Viz [[Codex CLI]].

Konkrétní pravidla, který model na jaký task, jsou v [[Výběr Modelu]].

---

## Co se změnilo

Dřív jsem jel čistě na Anthropic stacku: Sonnet na 90 % práce, Opus na plánování, Haiku na triviality v parallel agentech.

Dvě věci to rozbily:

1. **Haiku jsem přestal používat úplně.** Úspora tokenů nevyvážila kvalitu výstupu ani u těch nejjednodušších tasků. Dnes mám v [[Globální CLAUDE.md|CLAUDE.md]] tvrdé pravidlo *Never use Haiku*.
2. **gpt-5.6-sol převzal backend.** Kombinace štědrých limitů a vysoké intelligence znamená, že u serverové logiky, skriptů a migrací nemá smysl sahat po Claude modelu.

**Strategie orchestrátor + subagenti** platí dál, jen se změnilo obsazení: silný model naplánuje a rozdělí práci → subagenti (Codex nebo Sonnet podle typu tasku) implementují → orchestrátor zkontroluje výsledky.

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

> Ceny a limity se u všech poskytovatelů hýbou rychle. Ber to jako směr, ne jako aktuální ceník.

### OpenAI Codex

Dnes u mě není alternativa, ale **součást stacku** — viz [[Codex CLI]]. Limity jsou velkorysé a za tu cenu odvede největší objem práce ze všeho, co používám.

### Kimi 2.5

$20/měs, překvapivě dobrý výkon. Vhodná alternativa do $20 budgetu.

### Z.ai

Neskutečně velké limity. Kód není na úrovni Claude, ale **cena/výkon** je zajímavá pro méně náročné tasky.

### MiniMax 2.5

Prý dobrý poměr cena/výkon, osobně jsem nevyzkoušel.

### OpenCode Zen / Go

Subscripce přímo v OpenCode, umožní ti používat více modelů v jednom TUI. Viz [[Nástroje#OpenCode|OpenCode]].

---

## Co nedoporučuji

**API klíče + OpenRouter** - na první pohled flexibilní, v praxi drahé. Při reálném workloadu zaplatíš výrazně víc než za předplacenou subscripci.

---

## Důležitý mindset

> Buď připravený kdykoliv přejít k něčemu jinýmu.

Svět AI se hýbe extrémně rychle. Dnes nejlepší agent nemusí být nejlepší za půl roku. Netlp na jednom nástroji, sleduj co se děje a neváhej experimentovat.

Ostatně přesně tohle se mi stalo s Codexem: dlouho jsem ho odepisoval jako slabší alternativu a dnes na něm stojí polovina mého workflow.

---

*Viz také: [[Výběr Modelu]], [[Codex CLI]], [[Nástroje]], [[Claude Code - Tipy a Triky]]*
