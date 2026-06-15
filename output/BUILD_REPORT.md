# BUILD REPORT — Shinonome Akito Janitor AI Character Card

## 1. Overview
Production of a **Character Card V2** for **Shinonome Akito** (Project SEKAI: Colorful Stage! —
Vivid BAD SQUAD), with an embedded keyword lorebook, plus supporting research and world bible.
**Strictly SFW / age-appropriate** (Akito is a high-school minor): friendship, rivalry, bandmate,
family, and slice-of-life only. English. Canon-first, with clearly-labelled original additions.

## 2. Orchestration: plan vs. reality
The plan was a 5-wave, 24-subagent fleet (Sonnet for synthesis, Haiku for lookups). I launched
**16 research subagents in parallel** (Waves 1+2). **A session usage limit (reset 8:10pm UTC)
throttled most of the burst:** 4 agents finished and wrote files; the rest returned a
session-limit error with no output.

**Adaptation (logged):** rather than re-launch a fleet that kept hitting the cap, I (the
Orchestrator) completed the remaining research **directly** via WebSearch/WebFetch + cross-checking,
then did synthesis, drafting, QA, and assembly myself. This conserved the session budget and kept
canon fidelity. Note: direct WebFetch to Fandom/Sekaipedia returned HTTP 403, so WebSearch (which
surfaces sourced snippets) was the primary verification channel, prioritising Fandom → Sekaipedia →
NamuWiki.

## 3. Per-output summary
| File | Source | Notes |
|------|--------|-------|
| `research/a4_appearance.md` | Subagent A4 (completed) | Hair/eyes/outfits, card variants, color motifs |
| `research/a7_trivia.md` | Subagent A7 (completed) | Birthday 11/12, CV Imai Fumiya, dog-fear origin, foods, routine |
| `research/a8_quotes.md` | Subagent A8 (completed) | Representative voice lines across moods |
| `research/b8_vs_support.md` | Subagent B8 (completed) | Virtual Singers' street personas + support cast |
| `research/a1_biography.md` | Orchestrator (direct) | Timeline childhood→present, family, turning points |
| `research/a2_personality.md` | Orchestrator (direct) | Facade↔real switch, drive, insecurity, fear |
| `research/a3_speech.md` | Orchestrator (direct) | Pronoun/address terms, register, how to write him |
| `research/a5_relationships.md` | Orchestrator (direct) | Per-person dynamics (SFW) |
| `research/a6_music.md` | Orchestrator (direct) | Rapper/producer role, genres, philosophy, gear |
| `research/b6_radweekend.md` | Orchestrator (direct) | RAD WEEKEND + Nagi secret + RAD:BLAST |
| `research/b7_locations.md` | Orchestrator (direct) | WEEKEND GARAGE, Vivid Street, Crase Cafe, the Walls |
| `research/b1_b5_cast.md` | Orchestrator (direct) | Kohane, An, Toya, Ena, Ken (B1–B5 consolidated) |
| `worldbuilding.md` | Orchestrator (synth) | Canon world bible + 5 labelled original locations |
| `akito.card.json` | Orchestrator (assembly) | **Primary deliverable** — V2 + embedded lorebook |
| `akito.lorebook.json` | Orchestrator | Standalone lorebook (26 entries) |
| `akito.card.md` | Orchestrator | Human-readable every-field version |
| `build_card.py` | Orchestrator | Reproducible builder (single source of truth) |

## 4. Conflicts found & resolutions
1. **Who runs WEEKEND GARAGE — Ken or Mita?** The master prompt said Ken; subagent B8 (Sekaipedia)
   said Mita. **Resolution:** both, correctly — **Ken built and owns** WEEKEND GARAGE after
   retiring from RADder; **Mita Kotaro manages it day-to-day** for him and later coaches VBS
   full-time. Verified via WebSearch (Sekaipedia: Shiraishi Ken / Mita Kotaro).
2. **Ena's age ("25").** A search snippet called Ena "a 25-year-old artist" — a conflation with her
   unit's name *Nightcord at 25:00* (25:00 = 1 a.m., not an age). **Resolution:** Ena is Akito's
   **older sister by ~1 year**, a high-schooler — corrected everywhere.
3. **The RAD WEEKEND "secret."** Pinned precisely: RADder = **Ken + Kotaki Taiga + Nagi** (Taiga's
   sister); RAD WEEKEND was Nagi's **farewell stage** while she was terminally ill; Taiga later
   reveals this and crushes VBS in a battle — the blow that nearly made Akito quit. (Sources: STRAY
   BAD DOG story summary + VBS wiki pages.)
4. **Kohane's school.** She attends **Miyamasuzaka Girls' Academy**, not Kamiyama High (the others
   do). Corrected.
5. **Height/blood type.** Height appears as ~174 cm in some fan sources but is not consistently
   official; blood type undocumented. Kept out of permanent fields to avoid asserting unverified
   stats; appearance noted as "lean/athletic."

## 5. Canon-vs-original ledger
- **Canon [CANON]:** all character facts; the unit & members; BAD DOGS/Vivids; WEEKEND GARAGE;
  Vivid Street; Crase Cafe; the Street SEKAI and the Walls; RADder; RAD WEEKEND + Nagi's secret;
  RAD:BLAST/RaveN; Ken, Mita, Taiga/WALKER, Arata, EVER; the Virtual Singers' street personas; the
  dog phobia; appearance; school.
- **Original [ORIGINAL — non-canon]:** five everyday hangouts only — **The Backbeat** (late-night
  ramen counter), **Dawn Steps** (riverside training/writing spot), **Needle & Bolt** (record/gear
  shop), **Corner Stop** (24h convenience store), **Studio Lighthouse** (cheap practice room); plus
  minor roleplay gear flavor (sticker laptop, headphones). These add scene options and never
  override canon.

## 6. Final token budget (rough estimate; char/4 vs words×1.33)
| Field | ~Tokens | Budget | Status |
|-------|---------|--------|--------|
| description | 391 | 450 | OK |
| personality | 323 | 350 | OK |
| scenario | 126 | 150 | OK |
| **permanent subtotal** | **~840** | — | within budget |
| first_mes + 2 alt greetings | ~632 | — | shown only at greeting |
| mes_example | ~494 | — | few-shot anchor |
| lorebook (26 entries) | ~1,950 total | — | keyword-loaded, not permanent |

Encyclopedic detail lives in the **lorebook** (loaded by keyword), keeping the always-in-context
permanent fields lean.

## 7. SFW / age gate (Q2)
- Card content is friendship/rivalry/bandmate/family/slice-of-life; **no romantic or sexual content,
  no aging up.** `SFW` tag present; `system_prompt` and `post_history_instructions` hard-code the
  SFW guardrail and redirect romance attempts.
- An automated term scan flagged `sex / romantic / romance / aged up` — all **false positives**:
  they occur only inside the **guardrail wording itself** ("No romantic or sexual content," "never
  aged up"). No problematic content present.

## 8. Acceptance criteria
- [x] `akito.card.json` valid JSON, Character Card V2, imports cleanly (Janitor/Tavern).
- [x] SFW & age-appropriate; Q2 passed; no romance/sexual/age-up content.
- [x] Canon claims sourced (research files cite URLs); conflicts resolved & logged.
- [x] All four VBS members + Ena, Ken, Mita, Taiga, support cast, and the Virtual Singers appear.
- [x] World bible covers canon locations **plus 5 labelled original** ones.
- [x] Lorebook has 26 keyworded entries; canon vs original clearly marked.
- [x] Permanent fields within budget; detail pushed to the lorebook (Q4).
- [x] This report: per-output summary, conflicts + resolutions, ledger, token budget.

## 9. Note on completeness
Because the agent fleet was throttled mid-run, the research corpus was finished by the Orchestrator
directly rather than by 16 discrete agents. Coverage of the required topics is complete and sourced;
the per-file structure mirrors the intended agent outputs.
