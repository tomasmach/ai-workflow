---
tags:
  - ai-workflow
---

# Výběr Modelu

Který model na jaký task. Tohle je nejdůležitější rozhodnutí, které při AI-driven developmentu děláš opakovaně — a nejčastěji špatně.

> **Srpen 2026:** tahle stránka dřív stála na ranking tabulce (cost/intelligence/taste per model). Ta vznikla v éře GPT-5.5, kdy Claude orchestroval a Codex dělal jen mechanickou práci. S gpt-5.6-sol se svět otočil: **90 % mojí práce dnes jede v Codexu** a tabulku nahradilo jednodušší rozdělení rolí.

---

## Rozdělení rolí

**Codex (gpt-5.6-sol) je primární.** Je levný a chytrý, takže přes něj jde skoro všechno: backend, skripty, migrace, investigace, čtení kódu — a i malé UI úpravy typu „tohle tlačítko udělej takhle".

**Claude je specialista.** Nastupuje na:

- větší UI a designovou práci
- cross-planning napříč projekty
- nemilosrdnou kritiku a review
- situace, kdy výstup od Sola není ono

Je dražší, tak ho šetřím na věci, kde je potřeba vkus. Podklad pro tohle rozdělení dal audit mé historie: Claude sessions selhávaly na vkusu, Codex sessions na procesu — každý harness má smysl tam, kde neselhává.

---

## Automatické vzory

Věci, které jsem dřív psal ručně v každém promptu (audit našel 544 takových zpráv) a dnes je nese [[Globální CLAUDE.md]]:

- **Nemilosrdná kritika** — po každé větší frontend práci automaticky, čerstvým agentem
- **Dva nezávislé plány** — u větších návrhů dva modely, vzájemná kritika, syntéza
- **Fresh agent na code review** — nikdy ten, co kód napsal
- **Eskalace bez ptaní** — když výstup nestačí, přepiš to chytřejším modelem; eskalace stojí míň než odeslaná průměrná práce
- **Vzájemná delegace** — Claude posílá backend a čtení kódu Codexu (`codex exec -s read-only`), Codex navrhuje Claude na velký design

**Nikdy Haiku.** Bez výjimek, ani pod tlakem na cenu.

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

*Viz také: [[Codex CLI]], [[AI Agenti]], [[Context Management]], [[Globální CLAUDE.md]]*
