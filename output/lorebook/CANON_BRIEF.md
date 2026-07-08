# PJSK Lorebook Project — Shared Canon Brief

Read this file first. It fixes names, spellings, and unit rosters so all category
files stay consistent with each other. Cross-verify anything not listed here with
your own web research — this brief covers only roster/affiliation facts that were
confirmed against multiple independent sources before work began.

## Naming convention
Use Western name order (Given Family) as the primary display name in all files,
e.g. "Ichika Hoshino", "Akito Shinonome" — since that's how the global/EN release
and most fan wikis present them. You may note the Japanese order/kanji in the
content body if useful, but keep "key" arrays populated with BOTH orders plus
common nicknames/aliases so search matches regardless of phrasing.

## Confirmed unit rosters (do not deviate from this)

1. **Leo/need** — vocal-collective idol unit anchored around Hatsune Miku.
   Members: Ichika Hoshino, Saki Tenma, Honami Mizuhara, Shiho Hinomori.

2. **MORE MORE JUMP!** — cheerful idol unit anchored around Kagamine Rin & Len.
   Members: Minori Hanasato, Haruka Kiritani, Airi Momoi, Shizuku Hinomori.
   (Shizuku Hinomori is Shiho Hinomori's younger sister — cross-unit sibling link.)

3. **Vivid BAD SQUAD (VBS)** — street/band unit anchored around MEIKO, formed by
   the merger of two duos: "Vivids" (Kohane Azusawa, An Shiraishi) and "BAD DOGS"
   (Akito Shinonome, Toya Aoyagi). Members: Kohane Azusawa, An Shiraishi,
   Akito Shinonome, Toya Aoyagi.

4. **Wonderlands x Showtime (WxS)** — theatrical/musical-show unit anchored
   around KAITO, performs at the Wonder Stage in Phoenix Wonderland.
   Members: Tsukasa Tenma, Emu Otori, Nene Kusanagi, Rui Kamishiro.

5. **25-ji, Nightcord de. (Nightcord at 25:00)** — anonymous online music
   circle anchored around Megurine Luka, meets nightly around 1AM.
   Members: Kanade Yoisaki, Mafuyu Asahina, Ena Shinonome, Mizuki Akiyama.

**IMPORTANT — no member overlap between units.** Each of these 20 characters
belongs to exactly ONE of the five units above. There is NOT a shared-member
twist between VBS and Nightcord (that was an open question at project start;
research confirmed the two rosters are fully disjoint). Known cross-unit
*family/social* links (not membership overlap):
- Akito Shinonome (VBS) and Ena Shinonome (Nightcord) are siblings (Ena is
  about a year older).
- Saki Tenma (Leo/need) and Tsukasa Tenma (WxS) are siblings.
- Shiho Hinomori (Leo/need) and Shizuku Hinomori (MMJ) are siblings.
- Nene Kusanagi and Rui Kamishiro (both WxS) are childhood friends/neighbors.
Verify exact age/birth-order and any other cross-unit relationships yourselves;
the brief above is only to prevent miscasting someone into the wrong unit.

## The 6 Virtual Singers
Hatsune Miku, Kagamine Rin, Kagamine Len, Megurine Luka, MEIKO, KAITO. Treat
these as a "unit" category of their own alongside the 5 human units.

## Schools (verify details, but these anchors are confirmed)
- **Kamiyama High School** — the main/shared high school; most of the cast
  attends here (confirm exact per-character roster yourselves).
- **Miyamasuzaka Girls' Academy** — separate all-girls school; Kohane Azusawa
  attends here. Verify who else does.
Other schools/grades: verify per character — do not assume everyone attends
Kamiyama.

## Output format — SillyTavern World Info entry schema
Every entry your file contributes must be a JSON object with exactly these
fields (plus nothing else unless noted):

```json
{
  "key": ["Primary trigger keyword", "Alt name", "Nickname"],
  "keysecondary": [],
  "comment": "Short internal label for the entry, e.g. 'Character: Ichika Hoshino'",
  "content": "The paraphrased lore text itself. Original wording only.",
  "constant": false,
  "selective": false,
  "order": 100,
  "position": "after_char"
}
```

Rules:
- `key`: 4-10 relevant trigger words/phrases (full name, given name alone,
  nicknames, romaji variants, unit name if unit entry, place name if location
  entry, etc).
- `keysecondary`: leave as `[]` unless you deliberately want AND-logic
  disambiguation, in which case also set `selective: true`.
- `constant`: set `true` ONLY for foundational entries that should basically
  always be in context (e.g. "what is a Sekai", "the 5 units overview", core
  glossary terms). Leave `false` for everything else (character bios, single
  locations, individual songs, single costumes, etc).
- `order`: default `100`. You may bump foundational/constant entries to `150`.
- `position`: always the literal string `"after_char"` for consistency across
  the whole project.
- Do not include a `uid` field — the orchestrator assigns uids at merge time.

Each category file must be a **JSON array** of such entry objects (not wrapped
in an "entries" object — that wrapping happens at final merge).

## Hard rules (apply to everything you write)
- Use web search (and web fetch where it works — note that fandom.com and
  wikipedia.org may return 403 to direct fetch; rely on WebSearch's synthesized
  results and cross-check with at least two independent queries/sources per
  contested fact, plus sekaipedia.org, colorfulstage.com official site, and
  tvtropes.org as fetchable alternates) to verify accuracy.
- NEVER copy raw text from any source. Fully paraphrase everything in your own
  original wording, including story summaries and location descriptions.
- Do NOT include full song lyrics — narrative context only.
- For family/parents and bedroom description fields specifically: only state
  what is actually confirmed in official material. If unknown, write the
  literal string "not disclosed in canon" (family) or "not depicted in canon"
  (bedroom) rather than inventing anything.
- Keep content paraphrased, concise, and lore-accurate — a few sentences to a
  short paragraph per entry is plenty; this is a lorebook for AI roleplay
  context injection, not an encyclopedia article.
