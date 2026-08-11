---
tags:
  - ai-workflow
---

# Globální CLAUDE.md

Můj globální konfigurační soubor pro Claude Code - uložen v `~/.claude/CLAUDE.md`.

Platí napříč **všemi projekty**. AI si ho přečte automaticky na začátku každé session.

Viz [[Prompting#CLAUDE.md|jak CLAUDE.md funguje]].

> Ekvivalent pro Codex je `~/.codex/AGENTS.md` — od srpna 2026 jsou oba soubory **identické**, jeden text pro oba harnessy. Viz [[Codex CLI#Globální AGENTS.md|AGENTS.md]].

---

## Přepis v srpnu 2026: z config souboru na dopis

V srpnu 2026 jsem soubor kompletně přepsal podle procesu z videa [I made Claude smarter by writing it a letter](https://www.youtube.com/watch?v=e1snsuY4lTI) od Thea. Změnila se nejen pravidla, ale celý přístup:

**Z anglického config souboru se stal český dopis.** Dřív jsem psal instrukce anglicky a jazyk odpovědí řešil zvlášť. Jenže modely dělají tone-matching: když soubor zní jako dopis od konkrétního člověka, agent odpovídá jako člověku, ne jako ticketu. A protože s modely stejně píšu česky, píšu česky i soubor.

**Pravidla vznikla z auditu, ne z hlavy.** Před přepisem jsem nechal agenta projít celou moji session historii (254 Claude sessions + 4 162 Codex sessions) a spočítat, kde mě agenti reálně štvou. Výstup: Claude selhává na vkusu (odmítnuté UI), Codex na procesu (špatný nástroj, falešné „hotovo"). Každé pravidlo v souboru má za sebou konkrétní opakovanou frustraci — třeba 86 ručních spuštění `/humanizer` se přetavilo v pravidlo „prožeň humanizerem sám od sebe".

**Soubor přiznává, kdo jsem.** Úvod říká na rovinu: historií backend dev, technickým detailům do hloubky nerozumím, jsem extrémně líný. To nejsou přiznání, to je zadání — agent z toho pochopí, že nese techniku a verifikaci on a že se mnou má mluvit v důsledcích, ne v terminologii.

---

## Struktura souboru

Místo výpisu celého obsahu (109 řádků, průběžně se mění) struktura a co která sekce řeší:

| Sekce | Co řeší |
|-------|---------|
| Úvodní dopis | Kdo jsem, co stavím (Uprate, Na Pivo), dělba práce: agent nese techniku, já produkt a vkus |
| Jak se mnou mluvit | Česky, důsledky před terminologií, krátce, bez hedgingu, otázky jsou read-only |
| Mini glosář | Můj slovník: „Bro" je normální rejstřík, „proklikat" znamená reálnou verifikaci, co je Uprate/Na Pivo/vault |
| Obecné preference | Jednoduchost, YAGNI, cílené testy, oprav každou chybu na kterou narazíš, 2minutový limit na tiché operace |
| Stack | Existující repa podle sebe (PHP/Laravel, Expo + Django), nové projekty TypeScript + Next.js |
| Verifikace | Nikdy „hotovo" bez spuštění, screenshot + podívat se na něj, reprodukce bugu před „opraveno" |
| Vizuální práce | Mocky A/B/C před editací komponent, DESIGN.md je zákon, dark mode, žádný AI slop, humanizer automaticky |
| Delegace | Codex primární a levný, Claude na velký design a kritiku, nikdy Haiku. Viz [[Výběr Modelu]] |
| Blast radius | Co je svaté: produkce, App Store Connect, mazání větví, cizí procesy, vault |
| Git a PR | Worktree lifecycle s draft PRs, konvenční commity. Viz [[Git Workflow]] |
| Defaulty, ne zákony | Můj prompt přebíjí soubor, repo přebíjí globál |
| Poznámky pro Claude a Codex | Jediné harness-specifické sekce — každý ví, co je jeho parketa a co delegovat |

---

## Co se osvědčilo

**Glosář je pro výstup, ne pro vstup.** Agent mi rozuměl vždycky. Glosář je tam proto, aby mluvil zpátky mým jazykem — a aby věděl, že „Bro, tohle je špatně" není eskalace, ale úterý.

**Otázky jsou read-only.** Když se ptám „proč to tak je", chci odpověď, ne editaci souborů. Jedna z nejúčinnějších vět v souboru.

**Defaulty, ne zákony.** Bez téhle sekce se agent hádá s promptem, když se rozejde se souborem. S ní vyhrává prompt a je klid.

**Error Policy zůstala z minulé verze** — oprav každou chybu, na kterou narazíš, i pre-existing. Krátká věta s velkým dopadem.

---

## Velikost a údržba

109 řádků a držím to tam. Postup údržby à la Theo: všimnu si opakované frustrace → zeptám se agenta, proč se tak rozhodl → přidám nebo přiostřím jeden řádek → syncnu na ostatní stroje. Metrika úspěchu: prompty se zkracují.

---

*Viz také: [[Prompting]], [[Výběr Modelu]], [[Git Workflow]], [[Codex CLI]], [[Skills]], [[Memory a Hooks]]*
