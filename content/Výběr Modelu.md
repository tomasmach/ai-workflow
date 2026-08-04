---
tags:
  - ai-workflow
---

# Výběr Modelu

Který model na jaký task. Tohle je nejdůležitější rozhodnutí, které při AI-driven developmentu děláš opakovaně — a nejčastěji špatně.

---

## Tabulka

Hodnocení 1-10, vyšší = lepší. **Cost** odráží to, co reálně platím (OpenAI má hodně štědré limity), ne ceníkovou cenu. **Intelligence** je jak těžký problém modelu předhodíš bez dozoru. **Taste** pokrývá UI/UX, kvalitu kódu, návrh API a copy.

| Model | Cost | Intelligence | Taste |
|-------|------|--------------|-------|
| gpt-5.6-sol | 7 | 9 | 7 |
| sonnet-5 | 5 | 5 | 7 |
| opus-4.8 | 4 | 7 | 8 |
| fable-5 | 2 | 9 | 9 |

---

## Pravidla

**Cost je jen tiebreaker.** Když se osy dostanou do konfliktu u něčeho, co má jít do produkce, platí pořadí `intelligence > taste > cost`.

**Tabulka je default, ne limit.** Když výstup levnějšího modelu nesplňuje laťku, přepiš to dražším modelem bez ptaní. Eskalace stojí míň než odeslaná průměrná práce.

**Nikdy Haiku.** Bez výjimek, ani pod tlakem na cenu. Tohle je změna oproti dřívějšku, kdy jsem Haiku používal na triviální tasky v parallel agentech — nevyplatilo se, kvalita výstupu neodpovídala ani té nízké ceně.

---

## Podle typu práce

| Typ práce | Model | Proč |
|-----------|-------|------|
| Backend implementace | gpt-5.6-sol | Route handlery, DB/schema, server logika, skripty, migrace, CLI. Cokoliv bez UI vrstvy. Viz [[Codex CLI]] |
| Čtení a investigace | gpt-5.6-sol | Čtení kódu, grepování logů, trasování bugu. Levné a drží raw soubory mimo Claude kontext |
| Bulk / mechanická práce | gpt-5.6-sol (low effort) | Jasně zadaná implementace, analýza dat. Sol je silný i na low |
| UI, copy, tvar API | fable-5 nebo opus-4.8 | Potřebuje taste ≥ 7. Design judgment, ne implementace |
| Review plánu / implementace | fable-5 nebo opus-4.8 | Volitelně gpt-5.6-sol jako nezávislý třetí pohled |

**Laťka pro backend je vyšší než u ostatních typů:** i drobnost pošli přes Codex, nedělej ji potichu sám jen proto, že je „dost jednoduchá".

---

## Rozdělení rolí u UI

Tohle se plete: *rozhodnout, jak má vypadat veřejné rozhraní* a *implementovat ho* jsou dvě různé práce.

- Jak se API jmenuje, jak je strukturované a jak se s ním pracuje → taste model
- Postavit route za tím rozhraním → Codex

Codex to postaví, jen by neměl být ten, kdo rozhoduje, jak to má vypadat.

---

## Reasoning effort

U Codexu se volí per run přes `-c model_reasoning_effort="<level>"`:

- **low** — mechanická práce s jasným zadáním
- **medium** — default
- **high** — jen skutečně těžké problémy

Nikdy nejdi nad `high`. Config má vlastní default, proto flag posílej vždy explicitně.

---

## Jak modely spustit

- **Claude modely** (sonnet-5, opus-4.8, fable-5) — přes `model` parametr v Agent / Workflow
- **gpt-5.6-sol** — jen přes Codex CLI (`codex exec`, `codex review`). Viz [[Codex CLI]]

---

*Viz také: [[Codex CLI]], [[AI Agenti]], [[Context Management]]*
