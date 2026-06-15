# Shinonome Akito — JanitorAI build (correct format)

This folder is the **JanitorAI-native** version of the character, formatted to match the actual
**Create a Character** form and the **Script Making Guide** (Icehellionx) for lorebooks.

## Files
| File | What it is | Where it goes in JanitorAI |
|------|------------|----------------------------|
| `CHARACTER.md` | Copy-paste character fields | **General** tab (Title, Chat name, Bio) + **Definition** tab (Personality, Scenario, Initial messages, Example dialogs) |
| `akito_lorebook.js` | Sandboxed-JS "Everything Lorebook" | Your character's **Lorebook / script** field (the sandbox-script area the guide is written for). Paste the whole file. |

## How to use
1. **Create a Character** → **General**: upload an image, then paste **Title**, **Chat name**, **Bio** from `CHARACTER.md`.
2. **Definition**: paste **Personality** and **Scenario**. Add each **Initial message** as its own slot with the **＋** button (4 provided, up to 10 allowed). Paste **Example dialogs**.
3. Open the **Lorebook / script** area and paste the **entire** `akito_lorebook.js`. Save.
4. Start a chat. Mention canon names/places (Toya, Ken, RAD WEEKEND, WEEKEND GARAGE…) and the script feeds the right facts in; talk music to drop his polite mask; the mask also thaws on its own as the chat gets longer.

## What the lorebook script does (per the guide)
The guide's rule: a script may read the chat but may only **append to `context.character.personality` / `context.character.scenario`**. This script:
- **Everything Lorebook** (Ch. 13 & 17): canon facts grouped into categories (`unit`, `members`, `family`, `mentors`, `story`, `places`, `vsingers`, `self`); one match per category fires to keep the prompt lean.
- **Safe matching** (Ch. 4): lowercases + space-pads the message and uses `indexOf(" key ") !== -1`.
- **Progressive pacing** (Ch. 6): his polite mask thaws as `message_count` grows.
- **Combined triggers** (Ch. 8): music/competition keywords instantly flip him to his real, fired-up self.
- **Event lore** (Ch. 9): a small ~8% ambient street beat for atmosphere (easy to disable).
- The **dog** keywords fire his SFW comedic-panic gag.

## Sandbox safety (Ch. 3)
ES5 only — `var`, `for` / `for..in`, `indexOf`, `Math.random`, `new Date`. **No** arrow functions, template strings, `.includes`, `.map/.filter/.forEach` (those fail silently). It never touches read-only fields (name, example_dialogs, chat history).

## Keyword caveat
Space-padded matching can't catch a key glued to punctuation (e.g. `dog?`) and deliberately avoids bare common words (so An uses `shiraishi an`, not a bare `an`). This is the guide's documented trade-off — add more key variants if you want wider matching.

## SFW
Akito is a high-school minor. Everything here is friendship / rivalry / bandmate / family / slice-of-life. No romance or sexual content; the dog bit is a light gag. Never age him up; never reproduce copyrighted lyrics.

---
*The `../akito.card.json` (Character Card V2) is kept only as an optional **Tavern PNG import** alternative — the files in this folder are the correct JanitorAI format.*
