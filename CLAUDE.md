---
title: CLAUDE.md — pravidlá pre sessions v tomto repe
description: Prepojenie code sessions na Jánovu externú pamäť (Google Drive), aby Cowork aj kód zdieľali jeden kontext
tags: [claude, externa-pamat, session-log]
date: 2026-09-19
---

# Pravidlá pre Claude v tomto repe

Toto je Jánova (Ján Búci, Veselá veda Slovensko, jbuci17@gmail.com) pracovná kópia
bootcamp šablóny. `CONTEXT.md` v roote je ukážkový súbor autora šablóny (Jaro Satori) —
**nie je to Jánov kontext**, neriaď sa ním.

Jazyk: slovenčina, tykanie. Pri každom novom `.md` súbore pridaj YAML front matter
(title, description, tags, date).

## Externá pamäť — jeden zdroj pravdy pre Cowork aj kód

Ján používa externú pamäť — zložku `Claude_externa_pamat` na Google Drive. V Coworku
na Macu je namountovaná lokálne (`~/mnt/Claude_extern*`), z code sessions (cloud aj
lokálne) je dostupná cez Google Drive MCP. Všetko podstatné, čo sa v session vyrieši,
sa zapisuje tam — vďaka tomu Cowork aj code sessions vidia to isté a nič sa nerieši
dvakrát.

Kľúčové Drive ID:

| Zložka | ID |
|---|---|
| `Claude_externa_pamat` (root) | `1Nm53U9_zP6OjyYQJxLF6grgv-WFZhuJu` |
| `Poznámky` | `1QG3EumHb8k-rijYlKtKaFMNbnKs4WPBx` |
| `Poznámky/dennik` | `1Fk-HqGJlWY6sHjPnX4FP1cZeBeHscDNB` |
| `Poznámky/dennik/_session-log` | `193oueKkbUJujDhVCV-GnDQoZJRbGdUuX` |

### Na začiatku session (odporúčané)

Ak úloha nadväzuje na predchádzajúcu prácu, pozri si najnovšie záznamy v
`_session-log` (search_files s `parentId = '193oueKkbUJujDhVCV-GnDQoZJRbGdUuX'`,
zoradené podľa času) a prípadné tematické poznámky v pamäti — nech sa nerobí
odznova, čo už je vyriešené inde.

### Na konci session (povinné, ak vznikol podstatný výstup)

Zapíš session log do `_session-log`, keď v session vzniklo aspoň jedno z: hotový
výstup (kód, commit, dokument, analýza, nastavenie), rozhodnutie, trvalý fakt,
alebo otvorená vec, ktorá niekam pokračuje. Nezapisuj po bežnej otázke bez výstupu.

Zápis cez `mcp__Google_Drive__create_file`:

- `parentId`: `193oueKkbUJujDhVCV-GnDQoZJRbGdUuX`
- `title`: `YYYY-MM-DD_HHMM_kratka-tema.md` — čas **lokálny** (Europe/Bratislava;
  cloud kontajner beží v UTC, prepočítaj), názov bez diakritiky, kebab-case
- `contentMimeType`: `text/markdown`
- `disableConversionToGoogleType`: `true` (musí zostať .md súbor, nie Google Doc —
  agent skener na Macu číta .md)

Obsah súboru:

```
---
title: <téma jednou vetou>
description: Záznam zo session
tags: [session-log]
date: YYYY-MM-DD
---

**Riešilo sa**: <2–4 vety, o čo išlo a prečo>

**Výsledok**: <čo vzniklo, kde to je — pri kóde uveď repo, branch a commit>

**Otvorené**: <čo zostalo nedoriešené, na koho to čaká> (vynechaj, ak nič)

**Trvalý fakt**: <fakt, ktorý platí aj o mesiac> (vynechaj, ak nevznikol)
```

Pravidlá: vecne, po slovensky, krátko, žiadne AI frázy. Nekopíruj celé výstupy —
stačí odkaz (cesta v pamäti, repo + commit). Neuvádzaj osobné údaje rodičov, detí
a lektorov nad nutný rámec. Súbory v `_session-log` nemaž ani neupravuj — presúva
ich agent skener (beží 2× denne, 13:00 a 20:00).

Ak Google Drive MCP v session nie je dostupný, záznam vynechaj a povedz to Jánovi
jednou vetou.
