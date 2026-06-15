# Shinonome Akito — Janitor AI Character Card

A production-ready **Character Card V2** for **Shinonome Akito** (東雲彰人) from
*Project SEKAI: Colorful Stage! feat. Hatsune Miku* — unit **Vivid BAD SQUAD (VBS)**.
Imports cleanly into **Janitor AI** and is **SillyTavern**-compatible.

> **Strictly SFW & age-appropriate.** Akito is a high-school minor; the card frames every
> relationship as friendship, rivalry, bandmate, family, or slice-of-life. No romantic or sexual
> content. Canon-first, with a few clearly-labelled original everyday locations.

## Deliverables (`output/`)
| File | What it is |
|------|------------|
| **`akito.card.json`** | The card — V2 schema with an embedded keyword lorebook (`character_book`). |
| `akito.lorebook.json` | The 26-entry lorebook as a standalone file. |
| `akito.card.md` | Human-readable version of every field (for review/editing). |
| `worldbuilding.md` | VBS world bible — canon + 5 labelled original locations. |
| `research/` | Sourced research notes (one file per topic, with cited URLs). |
| `BUILD_REPORT.md` | Per-output summary, canon conflicts + resolutions, ledger, token budget. |

## How to use
1. In Janitor AI (or SillyTavern), **import** `output/akito.card.json`.
2. The embedded lorebook triggers VBS lore by keyword automatically.
3. To get past Akito's polite-stranger mask: be sincere, or talk music. (Don't bring a dog.)

## Rebuilding
`output/akito.card.json`, `akito.lorebook.json`, and `akito.card.md` are generated from a single
source of truth:

```bash
python3 build_card.py
```

## Sources
Canon was verified against the Project SEKAI Wiki (Fandom), Sekaipedia, and NamuWiki — each
`research/*.md` file lists the URLs it used. Invented content is tagged `[ORIGINAL — non-canon]`.
