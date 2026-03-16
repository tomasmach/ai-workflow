---
tags:
  - ai-workflow
---

# Pluginy a Rozšíření

Doporučené pluginy pro Claude Code. Jedině ty co reálně používám.

---

## Superpowers ⭐ Nejdůležitější

> Repozitář: [github.com/obra/superpowers](https://github.com/obra/superpowers)

Instaluje se globálně, funguje napříč všemi projekty.

**Co to je:** Kolekce *skills* - workflow šablon které se načtou do Claude Code a vedou ho přes osvědčené procesy. Místo toho aby AI improvizoval, řídí se strukturovaným postupem.

**Proč ho používám nonstop:**
- Nahrazuje nutnost psát složité systémové prompty
- Skills pokrývají nejčastější workflow (plánování, debugging, review...)
- Dá se rozšiřovat vlastními skills

**Skills které používám nejvíc:**

| Skill | Kdy ho použiji |
|-------|----------------|
| `code-review` | Po každé větší implementaci |
| `brainstorming` | Před novou featurou, exploruje požadavky |
| `systematic-debugging` | Při jakémkoliv bugu |
| `writing-plans` | Před komplexní implementací |
| `TDD` | Když chci test-first přístup |

**Jak spustit:** přirozeným jazykem nebo `/` v Claude Code, Superpowers skills se zobrazí automaticky.

---

## Simplify

Zkontroluje a zjednoduší právě napsaný kód. Odstraní zbytečnou komplexitu, sjednotí styl, zlepší čitelnost.

Spouštím vždy po Code Review.

- **Claude Code** má od nedávna vlastní `/simplify` přímo zabudovaný - používám ten.
- **Superpowers** mají vlastní `simplify` skill - použiju ho pokud pracuju v jiném nástroji než Claude Code.

---

## Co jsem zkoušel a nedoporučuji

**Samostatný Code Review plugin** žere příliš mnoho tokenů. Místo něho používám `code-review` skill ze **Superpowers**, který dělá totéž efektivněji.

---

## Pořadí po implementaci

```
Implementace → Code Review (Superpowers) → Simplify → Commit
```

---

*Viz také: [[Claude Code - Tipy a Triky]], [[Workflow Proces]]*
