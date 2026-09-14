# SKILL.md — *Dominating South Korea: Starting with a Golden Trait* · production playbook (V1)

**Purpose.** The single, deduplicated rulebook for turning this serial's raw chapters into a
publisher-grade English EPUB. This file holds the **skills**; `worklog.md` holds the **state**
(cycle log, ships, canon pins). Do not duplicate skills between the two — SKILL.md is the master
reference, worklog §8 is the history.

**Current at ship:** nothing shipped yet. Tree = 0 chapters · 33 payload files · 30 manifest items ·
6 spine entries · 5 NCX navPoints · 8 nav list items · 1 image (`cover-bg.jpg`) · 20 WOFF faces ·
3 character cards · 4 introduction cards · 27 glossary cards. Next image id: **id-02**. Next chapter:
**ch001** (NCX `num_6`, playOrder `6`).

**Provenance of these skills.** The pipeline below was inherited from the reader's previous novel and
rewritten for this book. **The previous novel's content is banned** — see `reference/README.md` and
§16. Its cast, invented companies, labels, songs, tours, stat panels and chapter map are not this
book's canon, and none of it may be cited as precedent for a translation choice.

**Operating skills (reader directive, always on).** **DEEP SCAN** — read every raw line and every
produced line for content, contradictions, names, punctuation and block context, before and after
drafting. **DEEP THINKING** — reason about which style block owns each context, resolve raw-internal
contradictions deliberately, and fill thin context from understanding rather than dropping it.
**Style-block maximalism** is policy (§5).

**Update protocol — MANDATORY before every packaging:** refresh the *Current at ship* line, fold any
learned rule into the right section (merge, never append a duplicate), and add the ship's hash to
worklog §8. SKILL.md is versioned by its *Current at ship* line only.

---

## 1 · Workspace map

| Path | Role |
|---|---|
| `SKILL.md` | this playbook (skills) |
| `worklog.md` | state: §0 read-first summary, §8 cycle log newest-first |
| `WORKSPACE_SETUP.md` | what has been verified, and how to re-verify it |
| `AGENTS.md` | short read-first handoff for a fresh session |
| `work_epub/` | **the book**: `mimetype`, `META-INF/container.xml`, `OEBPS/{content.opf,toc.ncx,text/,images/,fonts/,styles/}` |
| `raws/` | untouched source raws, saved first (`raws/README.md`) |
| `image-search/` | image workbench: search downloads, generation originals, coding rules (`image-search/README.md`) |
| `reports/` | generated audit output (safe to delete; `workspace_audit.py` rebuilds it) |
| `reference/peninsula-inherited/` | the previous novel's SKILL/worklog/setup — **process only** |
| `fonts.css`, `stylesheet.css` | the reader's supplied references — never edit their bytes |
| `validate_tree.py` `punct_quotes.py` `repeat_check.py` `audit_marks.py` | house gates |
| `legacy_firewall.py` | bleed gate for the previous novel's content (hard) and raw-sourced real names (soft) |
| `sync_styles.py` `install_fonts.py` `style_index.py` | asset installers and the class-vocabulary index |
| `workspace_audit.py` | read-only full audit; regenerates `reports/`; tolerates an unbuilt package |
| `build_epub.py` | packer — **overwrites the root deliverable**; never run to inspect |
| `.sl.json` + `stylelint@16` | CSS lint (`npm ci --ignore-scripts --no-audit --no-fund` each cycle; node_modules is not persisted) |

**Book structure is fixed by the reader:** `Cover → Synopsis → Contents → Character Info →
Introductions → Glossary → Chapter 1 → …` That is the spine order, and `workspace_audit.py` fails a
tree whose spine opens with anything else. The Contents page is `text/nav.xhtml` (EPUB 3 nav, styled
by sheet section 38); `toc.ncx` mirrors everything except the nav itself.

---

## 2 · The per-chapter cycle (order of operations)

0. **Save the raw FIRST.** Untouched text to `raws/chNNN_raw.txt` (three digits) before recon,
   drafting or image work. A re-paste is saved as `chNNN_raw_v2.txt` and diffed; source custody is
   never overwritten.
1. **Recon.** Grep the tree for every named entity, callback and block this raw touches — canon greps
   BEFORE writing. Sample the exact markup of any block to reuse (`reports/style_index.md` lists
   every class and its section). Grep `raws/` for the first appearance of anything continuity-sensitive.
2. **Draft** `work_epub/OEBPS/text/chNNN.xhtml` in ONE `write_file` call. Chapter skeleton:
   xml decl → `<!DOCTYPE html>` → `<html>` with xhtml + epub namespaces → head (title, `fonts.css`
   then `stylesheet.css`) → `body > div.page-wrapper` → `header.chapter-header`
   (`p.chapter-number` + `h1.chapter-title` + `hr.chapter-rule`) → `div.location-stamp` → body blocks
   → close. Copy `ch001.xhtml` verbatim as the template once it exists.
3. **Images** (only when a context earns one): §7. Source files stay in `image-search/`; coded files
   go to `OEBPS/images/` and get a manifest `<item>` with the next numeric id.
4. **Wire-up** (§8), ET-parsing every touched file after each edit.
5. **Gates — ALL of §9, every touched chapter.** Fix and re-run until clean. No gate is optional,
   and `legacy_firewall.py` is a gate.
6. **Worklog §8 entry + §0 refresh** before packaging — no build without a log entry.
7. **Build** (`python3 build_epub.py`) → in-archive asserts (§11) → refresh SKILL.md *Current at
   ship* → seal the hash into worklog §8.
8. **Publish (standing reader directive).** Commit the final EPUB plus the tree, tooling and useful
   reports; `git push origin arena/01a09e8b-dominating-south-korea-startin`; verify
   `git rev-parse HEAD` equals `git rev-parse origin/arena/01a09e8b-dominating-south-korea-startin`;
   give the reader the GitHub download link
   (`https://github.com/DKILLER123/Dominating-South-Korea-Starting-with-a-Golden-Trait/raw/<sha>/<file>.epub`).
   Never force-push; never change `main`.

---

## 3 · Translation & voice standards

- **Source language.** This serial's raws are Simplified Chinese. Translate the Korean setting into
  English directly; never round-trip through Korean, and never leave Chinese surface forms behind.
- **Language.** English publisher grade. No machine-translation cadence; no speaker-name tags
  before dialogue (`张三：` style is converted to action-beat attribution); no "he said she said"
  ladders where the raw uses beats.
- **Dialogue.** Natural, emotionally resonant, K-drama/light-novel register. Curly `“ ”` for all
  speech and quoted matter — straight double quotes are forbidden in prose. Curly apostrophe `’` in
  text nodes (attributes keep straight quotes; `punct_quotes.py` and the setup normalizer handle this).
  Em-dashes for cut-offs stay flush inside quotes (`“I—”`).
- **Question marks.** Every true interrogative carries `?` — a flattened question is the #1
  AI-translation tell. Wh-clefts and temporal clauses are statements and keep periods: triage, never
  blind-fix. Raw `嗎 / ？ / ？？` restore their `?`. Incredulity is `?!`, never `??`; a run of `???` is
  the sanctioned fan-board idiom (`audit_marks.py` flags exactly-two, exempts three-plus).
- **Spelling.** US English throughout — color, labeled, romanization, license, defense. The inherited sheet is written in US style ("Chapter header … colorful", "solid color fallbacks"), so mixing in British forms mid-book reads as two translators. One pass, one register.
- **Honorifics preserved** where the raw has them: `-nim`, `-ssi`, `-yang`, `-gun`, `eonni`, `noona`,
  `oppa`, `hyung`, `sunbae`, `hubae`, `seonsaengnim`, `hoejang-nim`, `sa-jang-nim`, `geomsa`.
  Romanize per Revised Romanization, hyphenate suffix joins, and gloss a term on the glossary page
  the first cycle it is used (§12). Korean words stay Korean — do not smooth them into "sir"/"ma'am".
- **Protagonist.** **Bae Do-yoon** ( Korean order, family name Bae). The raw writes him `裴云`;
  this book never prints the Chinese rendering, "Pei Yun", or a shortened "Bae Yun"/"Do-yun".
  Never rename or localize him. Nicknames only if a chapter bestows them.
- **Stage names.** Entertainers are written by the name their industry and the raw use, not by their
  family name: `郑秀妍 → Jessica`, `林允儿 → Yoona`, `郑秀晶 → Krystal`. The pattern is
  *given name* (`Soo-yeon`) with the legal family name in parentheses once, on the card
  (`Jung Sooyeon`), and the stage name everywhere in prose. Never flip to the family name mid-chapter,
  and never let a card's parenthetical legal name become the running name.

- **Names.** Real people keep their real romanization **only when this book's raw names them**
  (`legacy_firewall.py` proves it). Fictional figures stay fictional and get their own cards. Never
  import a name from the previous novel as a convenience.
- **Chinese removal.** Zero Han characters, zero CJK punctuation (`【】`, `，`, `。`) in final text —
  gate-enforced. Drop site ads, watermark residue, stray numerals, author's platform footers. CN-net
  slang de-slanges: `霓虹`→Japan, `漢城`→Seoul. A classical-Chinese quotation is paraphrased in the
  author's voice inside an `author-aside`; the characters themselves are never printed.
- **Tone.** Adults behaving like adults. Intimacy non-graphic: suggest, then cut away. Sensitive
  content stays in the outline but is rendered tastefully; no moralizing, no hedging lectures.
- **Freshness.** No recycled phrasings, sentence shapes or imagery between chapters. Vary paragraph
  rhythm. Avoid LLM slop ("couldn't help but", "a testament to", "the air was thick with").

---

## 4 · Canon management

- **The tree is the canon.** Once a chapter is in the book, it outranks the raw that produced it.
  Before importing a raw beat, grep for it. If the raw contradicts an in-tree fact, the tree wins and
  the re-cut is logged in worklog §8.
- **No canon before the raw.** Nothing in `synopsis.xhtml`, `characters.xhtml`, `introductions.xhtml`
  or this file is a license to invent a date, age, height, title, relationship or event ahead of the
  chapter that states it. Those pages say only what the synopsis they were seeded from says.
- **Raw-internal contradictions.** When the raw disagrees with itself (a dress color, a time, a
  number of people in a room), keep the version the established setup supports and log the re-cut.
- **Timeline.** Maintain internal dates over raw stamps. For travel, verify booking lead time,
  duration and time zones in one basis; label local zones and flashbacks. Do not silently move a
  published chapter's clock to make a new scene fit.
- **New characters.** Full card on `characters.xhtml` (§12) + introduction card on
  `introductions.xhtml` when the figure is a recurring presence, one in-chapter `char-intro-block` at
  the first narrative mention, and a glossary entry only for a term the prose uses.
- **System/trait labels.** Keep one canonical form for every ledger phrase and never vary it: the
  trait is **Favor of Rich Women**, grade **Golden**, and an acquisition line reads
  `Acquired — Trait:` with the em-dash. If the raw of Chapter 1 settles a different wording, that
  chapter's wording wins and every later chapter follows it (log the pin).
- **Alternate history is fiction.** Real people and companies appear inside an invented timeline:
  never rewrite the fiction to match real-world biographies, and never assert a real person's conduct
  as fact in a front-matter page.

---

## 5 · Style-block catalog (single source of truth)

Reuse before creating. **Style-block maximalism is policy:** every context the raw gives gets the
block that owns it — even where the raw is only a few lines thick, keep the block and fill the rest of
the context from Deep Thinking (in-fiction, canon-safe). Every block is labeled by its own header
line. Canonical vocabularies are below; the machine-generated full list lives in
`reports/style_index.md` / `.tsv` (`python3 style_index.py`). All blocks live in
`work_epub/OEBPS/styles/stylesheet.css`; section numbers in brackets.

**Chapter furniture:** `chapter-header` (`chapter-number` · `chapter-title` · `chapter-rule`) [04,
Cardo 700 titles] · `location-stamp` (`ls-date` · `ls-place` · `ls-sub`) [06] · `scene-break` [07] ·
`dialogue-line` · `thought` · `highlight`/`highlight2`/`sound-effect` [05] · `pullquote` [16, cream
card, EB Garamond italic, Cardo drop-quote, tri-color ribbon] · `author-aside` (`aa-label` ·
`aa-text`; **label text must differ every chapter**) [53] · `chapter-divider` [18].

**Game/system:** `system-block` (`sys-header` · `sys-line`>`sys-key`+`sys-value` · `sys-note` ·
`sys-ding` · `sys-stat`>`sys-stat-line`>`sys-stat-label`+`sys-stat-value`) [10] · `notification` [11] ·
`status-panel` (`sp-header` · `sp-subject` · `sp-total` · `sp-row`>`sp-label`+`sp-value` · `sp-bar`>`.filled` ·
`sp-note`) [37] · `dev-quest` (`dq-header` · `dq-principle` · `dq-basis`>`dq-basis-key`+`dq-basis-val` ·
`dq-task`>`dq-num`+`dq-what`+`dq-gate` · `dq-reward`) [50] · `award-block` [39] · `release-block`
(`rs-header` · `rs-chip` · `rs-tier` · `rs-note`) [55].

**Media & social:** `app-screen` (`app-title` · `app-meta`) [13] · `chat-container` (`chat-header` ·
`chat-name` + `.self` on the SENDER only — the owner of the window, whose bubbles are `chat-sent` and
right-floated; every `chat-sent` name span MUST carry `.self` · `chat-bubble chat-sent`/`chat-received` ·
`chat-meta` · `chat-clear` · `chat-sticker`) [27] · `phone-call` [12: `pc-head` first child,
`pc-me` this end, `pc-them` far end, `pc-note` stage direction; `.sinister` variant for bad calls;
one-sided calls carry `pc-me` only] · `official-statement` (`os-masthead` · `os-meta` · `os-title` ·
`.os-note`) [24] · `official-post` (`op-band` · `op-handle` · `op-body` · `op-meta`) [43] ·
`news-digest` (`nd-headline` · `nd-source`) [25] · `comment-thread` (`comment-header` ·
`comment-item`, each opening with an inline `comment-floor` chip; the handle and the text stay inline in the item, there is no user/text class) [14] · `fanclub-block` (`fc-header` ·
`fc-post`>`fc-user`+`fc-text` · `.mod`/`.founder` · `fc-modnote`) [45] · `trend-block` (`tr-*`) [26] ·
`briefing-block` (`bf-band` · `bf-title` · `bf-source` · `bf-item`>`bf-key` · `bf-note`) [40].

**Scene cards:** `performance-block` (`pf-header` · `action-beat` · `beat` **only** — a fourth child class does not exist and must not be invented)
[09] · `variety-block` (`vt-header` · `vt-tag` with the sheet's only color modifiers `.red`/`.yellow`/.blue · `vt-mission` · `vt-verdict.safe` · `vt-caption` · `vt-rule`)
[33] · `recording-block` (`rec-header` · `rec-time` · `rec-voice`/`rec-voice2` · `rec-dot` · `rec-note`)
[23] · `studio-block` (`st-header` · `st-row`>`st-label`+`st-value` · `st-note`) [28] ·
`placement-reel` (`pr-header` · `pr-show` · `pr-item` · `pr-note`) [28.5] · `call-sheet` (`cs-header` ·
`cs-row`>`cs-time`+`cs-what` · `cs-unit`/`cs-unit-what` · `cs-unit-tag` · `cs-note`) [49] ·
`acting-block` (`ac-slate` · `ac-heading` · `ac-line` · `ac-cue` · `ac-direction` · `ac-note`) [41] ·
`lesson-block` (`lsn-header` · `lsn-term`>`lsn-gloss` · `lsn-step`>`lsn-count` · `lsn-note` ·
`lsn-teacher`) [51] · `menu-block` (`mn-header` · `mn-sub` · `mn-course` · `mn-dish` · `mn-desc` ·
`mn-rule` · `mn-note`) [56] · `wardrobe-block` (`wd-header` · `wd-sub` · `wd-tag` · `wd-label` ·
`wd-effect` · `wd-note` · `wd-photo` · `wd-item` · `wd-city` · `wd-country` · `wd-globe`) [20] ·
`hand-note` (`hn-label`; `.reply` variant) [22] · `hand-letter` (`hl-label` · `hl-sign`) [32] ·
`memory-block` (`mb-label` · `mb-voice`; `.bright` variant) [30] · `whisper-block` (`wh-label` ·
`wh-voice` · `wh-reply` · `wh-note` · `wh-close`; strict voice/reply alternation, **`wh-close` last**) ·
`lyric-block` (`lb-header` · `lyric` · `lb-note`) [08] · `screen-view` (`sv-header` · `sv-scene` ·
`sv-line` · `sv-caption` · `sv-note`) [44] · `pitch-deck` (`pd-title` · `pd-firm` · `pd-rank` ·
`pd-slide` · `pd-choice` · `pd-position` · `pd-strength` · `pd-foot` · `pd-mark`) [52] ·
`checklist-block` (`ckl-band` · `ckl-step`>`ckl-count` · `ckl-note`) [54] · `box-office`
(`bo-header` · `bo-title` · `bo-row`>`bo-rank`+`bo-label`+`bo-figure` · `bo-note`) [42] ·
`contract-block` (`ct-header` · `ct-clause` · `ct-figure` · `ct-note`) [21] · `world-dispatch`
(`wd-globe` · `wd-country` · `wd-city` · `wd-sub`) [34] · `finance-block` [17] · `hate-wall` (`hw-header` · `hw-scrawl` ·
`hw-note`) [31] · `lecture-block` (`lect-header` · `lect-q`) [15].

**Analysis cards:** `dossier-block` (`dg-header` · `dg-field`>`dg-label`+`dg-value` · `dg-note` ·
`dg-flag` · `dg-transcript`>`dg-transcript-label` · `dg-msg`; **values left-aligned**) [29]. A character's private reckoning is labeled as such —
not presented as a new magical system event.

**Front-matter pages:** `cover-shell`/`cover-overlay`/`cover-eyebrow`/`cover-title`/`cover-subtitle`/
`cover-ornament`/`cover-meta`/`cover-edition` [35] · `char-card` > `char-infobox`
(`ci-name` · `ci-photo` · `ci-caption` · `ci-table`) + `char-bio`, closed by `char-note` [36] ·
`char-intro-block` (`ci-tag` · `ci-body`>`ci-name`+`ci-role`+`ci-group`+`ci-born`+`ci-desc`) [46] ·
`toc-wrap` [38] · `glossary-wrap`>`glossary-hero`(`glossary-kicker` · `glossary-deck` ·
`glossary-rule` · `glossary-update`) · `glossary-index` · `glossary-note`>`gl-note-text` ·
`glossary-section`+variant(`suffixes`/`seniority`/`workplace`/`family`/`social`/`expressions`)
>`gs-title`+`glossary-grid`>`glossary-card`(`gl-term`+`gl-hangul` · `gl-card-text`>`gl-meaning`+`gl-use` ·
`gl-example`) · `glossary-footer`>`gl-footer-text` [48].

---

## 6 · New-block & font protocol

1. **Grep the sheet first.** `reports/style_index.md`, or
   `grep -n "selector" work_epub/OEBPS/styles/stylesheet.css`. The inherited trap is real: a new
   section was once drafted for a block that already existed.
2. If genuinely new: add a **numbered CSS section with a header comment** (context, class vocabulary,
   degrade behavior), scope child classes under the parent selector, and add a narrow-screen override
   beside the other `@media (max-width: 30em)` rules. New sections go at the end of the sheet so the
   inherited section numbers stay stable.
3. **Never edit an inherited rule** to make a chapter fit — `sync_styles.py` asserts rule identity and
   will fail. Mutating the shared sheet is allowed only for a genuine, documented defect, in which case
   `sync_styles.py`'s assert must be widened deliberately in the same commit and the deviation recorded
   in worklog §8.
4. New font required → `npm install @fontsource/<family>`, add the face mapping to
   `install_fonts.py`, verify glyph coverage with
   `.venv/bin/python install_fonts.py --verify` **before** committing, then add the `@font-face`
   (in the tree's `fonts.css` only — never in the reader's root reference file) and the manifest
   `<item>`, and note the license (all faces SIL OFL 1.1). Unused faces stay if they are fallbacks.
   Digits in titles must be lining. Measured at setup (`install_fonts.py --verify` prints the table):
   **Cormorant Garamond 600/700 and IM Fell English draw oldstyle digits**, so numerals never go in
   them — IM Fell carries no `lnum` at all, and Cormorant's `lnum` cannot be trusted through an EPUB
   reader. **Cardo 700 draws lining digits at cap height with no feature dependency**, which is why it
   owns `.chapter-title`; Lora, Crimson Pro, Inter, Courier Prime, Libre Baskerville and EB Garamond
   Italic also measure lining, and Caveat is "unclear" by nature (handwriting only, never a numeral
   carrier). A new display face has to pass this same measurement before it can carry numerals.
5. Re-run stylelint + `validate_tree.py` after every CSS edit. Stylelint config is `.sl.json`
   (reconstructed for this repo; `no-extra-semicolons` no longer exists in stylelint 16, and
   `declaration-block-no-redundant-longhand-properties` is off because the reference sheet is
   preserved byte-for-byte).

---

## 7 · Image pipelines

Everything about an image round starts and ends in `image-search/` (see its README): searches are
saved, sources are kept, and only the coded file is installed into the tree.

**Character portraits (real people).** `image_search` for a real photograph — close crop, portrait
aspect, preferably not watermarked. Center-crop 4:5 → 736×920 → JPEG q85 optimize →
`OEBPS/images/char-{name}.jpg` → manifest `<item id="id-NN">` → the card's `ci-photo`. Provenance
lives in worklog only, never printed in the book.

**Fictional figures.** Illustrate rather than fake a likeness (cover art included: `generate_image` →
keep the original in `image-search/` → code to the card spec → install). An illustration is labeled
as an illustration on the card caption; a photograph is never invented for a real person.

**Wardrobe plates.** Trigger: a *new* outfit with narrative intent (the same outfit twice = no plate).
Identity source order: (1) a reader-supplied file in `image-search/`; (2) the person's canonical
in-tree portrait. Without a suitable identity source, **skip the plate and the block** rather than
fabricate a likeness. Generate → center-crop 4:5 → 1120×1400 → JPEG q85 →
`images/wd_{who}_{garment}.jpg` → manifest id → `wd-photo` embed.

**Cover plate.** `images/cover-bg.jpg`, 1200×1800, JPEG q85 progressive, referenced by section 35's
`background-image` AND declared as `<item id="id-01" properties="cover-image">`; keep the top third
clear of focal detail because the title overlay sits there. v1 is installed and was inspected in the
tree, not just as generated.

**Numbers.** Record installed byte sizes in worklog §8. Next numeric image manifest id = last + 1
(currently **id-02**). Image count = declared `image/*` manifest items.

---

## 8 · Wire-up checklist (per chapter)

1. `content.opf`: `<item id="chNNN" href="text/chNNN.xhtml" media-type="application/xhtml+xml"/>`
   before `</manifest>`; `<itemref idref="chNNN" linear="yes"/>` after the previous chapter (or after
   `glossary` for ch001); bump BOTH `dc:description` stamps
   (`Volume One · Chapters 1–NNN` and `English publisher's edition of Chapters 1–NNN…`); add any new
   image/font items.
2. `toc.ncx`: `<navPoint id="num_{NNN+5}" playOrder="{NNN+5}">` after the previous chapter's block
   (five leading reference entries: **navPoints = chapters + 5**).
3. `text/nav.xhtml`: one `<li><a href="chNNN.xhtml">…</a></li>` after the previous chapter, before the
   `<!-- CHAPTER ENTRIES -->` tail comment (**nav list items = chapters + 8**: 5 reference entries +
   chapters + 3 landmarks). Once ch001 exists, repoint the `bodymatter` landmark at `ch001.xhtml`.
4. `cover.xhtml`: `#chapters-stamp` text → `Chapters 1–NNN`. `glossary.xhtml`: `.gl-footer-text` line 1
   → `Glossary updated through Chapter NNN`.
5. `characters.xhtml`: extend touched bios by exact-anchor `str.replace` (never index math); new cards
   go **before** the closing `char-note`. `introductions.xhtml`: append a `char-intro-block` card for a
   newly introduced recurring figure, before its `char-note`.
6. `glossary.xhtml`: append a `glossary-card` to the right `glossary-section` for every honorific or
   Korean term this chapter uses for the first time (`lang="ko"` on the Hangul gloss only).
7. ET-parse every touched file after every edit.

**Expected count deltas for one chapter and no new assets:** tree files +1 (34), manifest +1 (31),
spine +1 (7), navPoints +1 (6), nav li +1 (9). Recompute if images, fonts or new reference pages land.

---

## 9 · Pre-package gates (ALL mandatory, every touched chapter)

| Gate | Command (from the repo root) | Clean means |
|---|---|---|
| Tree/refs/classes | `python3 validate_tree.py` | PASS, 0 undefined classes, 0 unresolved refs, 0 CJK outside sanctioned `lang="ko"` glosses |
| Quote integrity | `python3 punct_quotes.py` | 0 files to rewrite |
| Repeats | `python3 repeat_check.py chNNN.xhtml` | 0 internal / 0 cross-chapter 8-grams; deliberate repeats (lyrics, drills) documented in worklog §8 |
| **Question-mark audit** | `python3 audit_marks.py work_epub/OEBPS/text/chNNN.xhtml` | no genuine NO-QM? flags after triage; no `”?`/`??`/` ?`/`?”.` malformations — **standing directive** |
| **Phone-call audit** | in `audit_marks.py` | `pc-head` is the first child; body classes ⊆ `pc-me`/`pc-them`/`pc-note` — **standing directive** |
| **Style-block deep scan** | re-read the finished chapter against §5 and the raw | every raw context owns a block; nothing the catalog covers is left in plain prose — **standing directive** |
| **Firewall** | `python3 legacy_firewall.py --json reports/firewall.json` | 0 hard hits; every soft hit cleared by `raws/` provenance or an allowlist line — **standing directive (reader)** |
| **Style-block coverage (machine)** | `python3 style_audit.py --json reports/style_audit.json` | PASS: ≥8 distinct block types per chapter, ≤0.25 blocks per prose word, no block type repeated in a chapter outside the device allowlist — **standing directive** |
| Stylesheet integrity | `python3 sync_styles.py` | `= … already current` + rule-identity check PASS |
| Font integrity | `.venv/bin/python install_fonts.py --verify` | 20 faces resolve; no missing critical glyphs |
| CSS lint | `npm ci --ignore-scripts --no-audit --no-fund` then `node_modules/.bin/stylelint --config .sl.json "work_epub/OEBPS/styles/*.css"` | 0 errors |
| XML parse | `python3 -c "import xml.etree.ElementTree as ET,sys,glob; [ET.parse(f) for f in glob.glob('work_epub/OEBPS/**/*.xhtml', recursive=True)]"` | no exception |
| CJK scan | inside `validate_tree.py` | 0 Han, 0 CJK punctuation in prose |
| Doubled words | `\b(\w+) \1\b` scan (also in `workspace_audit.py`) | none (laughter `ha ha` = false positive) |
| Metrics | `python3 workspace_audit.py --assets` → `reports/chapter_index.tsv` | dashes ≤ ~5/1k · longest paragraph ≤ ~100 words · `“`/`”` parity equal |
| Full audit | `.venv/bin/python workspace_audit.py --assets` | `structural_errors: []`; editorial flags triaged |

A zero exit from `workspace_audit.py` means integrity passed, not that editorial heuristics are
silent. Heuristic output is a to-read list, never an auto-fix instruction.

---

## 10 · Metrics bands (house style)

Dash density ≤ ~5 per 1,000 words after surgery (keep speech cut-offs, canonical
`Acquired — Trait:` labels and structural `mn-`/`ac-` dashes). No paragraph over ~100 words: split
monologues at seams, and a one-line reaction beat is a valid splitter. Punctuation: curly quotes
balanced, ellipses for trailing thoughts, `?` on every interrogative. Chapter length: whatever the raw
needs — never truncate, never pad to a word count.

---

## 11 · Build, seal & verify

1. `python3 build_epub.py` → record entries, bytes, sha256.
2. In-archive asserts (open the ZIP, do not trust the packer's stdout): `mimetype` first and STORED
   with exact bytes; `<item id="chNNN">` present; both `dc:description` stamps correct;
   spine = chapters + 6 in the mandated order; navPoint count = chapters + 5 with contiguous
   `playOrder`; nav `<li>` = chapters + 8; glossary footer stamp; chapter content spot-strings;
   **images byte-identical to the tree**; QM/phone-call fixes present in the packed bytes.
3. Tree↔archive name diff must be **empty** and every payload must match
   (`workspace_audit.py` prints `archive_only` / `tree_only` / `changed_files`). `work_epub/mimetype`
   is a real canonical member — compare it too, never "fix" it by deleting it.
4. Record the ship (entries, bytes, sha256 prefix) in worklog §8 + §0, bump SKILL.md's
   *Current at ship*, then commit/push per §2 step 8 and `present_file` the EPUB with the GitHub link.

---

## 12 · Front-matter page contracts

- **`characters.xhtml`** — one `char-card` per person, `id="char-{name}"`, holding `char-infobox`
  (`ci-name`, optional `ci-photo`, one-phrase `ci-caption` epithet, `ci-table` rows: Role / Field /
  Born / Education / Occupation / Patron / Group / Agency / In the story / Status) then `char-bio`
  (`h3` "In this story" + paragraphs). New cards before the closing `char-note`; bios only ever grow by
  append. The `char-note` carries the likeness/rights sentence covering all portraits.
- **`introductions.xhtml`** — cast showcase in the section-46 vocabulary: `ci-tag` = one-word role
  stamp (Lead / Idol / Patron / System), `ci-role` = the line a reader should remember, `ci-group`,
  `ci-born` = what the story says about them so far, `ci-desc` = how they enter. Facts stay on the
  character card; this page is the first impression.
- **`synopsis.xhtml`** — the book's own words only, from `raws/Synopsis_raw.txt`, plus the trait card
  (`system-block`), the ultimatum (`dev-quest`), and the edition's facts (`dossier-block`). No chapter
  plot is summarised here.
- **`glossary.xhtml`** — every term gets `gl-term` + romanization + optional
  `<span class="gl-hangul" lang="ko">` gloss, `gl-meaning`, `gl-use`, one `gl-example` sentence in the
  book's own voice. `lang="ko"` is the only sanctioned way to print Hangul and is never used in a
  chapter file (`validate_tree.py` enforces both halves of that).
- **`nav.xhtml`** — Contents is a real page, not only a hidden nav: five reference entries, then
  chapters in reading order, then the three landmark items.
- **`cover.xhtml`** — `#chapters-stamp` is the only per-cycle text on the page.

---

## 13 · Worklog discipline

- **§8 entry before build, always** (Source & scope · Canon held / re-cuts · Blocks · Wire-up · Gates ·
  Ship). Newest first. Multi-line anchors matched with whitespace-tolerant regex, not literal find.
- **§0 refresh** every cycle: chapter count, stamps, images, fonts, cards, ship hash, new directives.
- Errors and dead ends get one line each in §8 or §14 — a future cycle must not relearn them.
- Every seeded or pending fact is written as "pending raw" rather than as canon.

---

## 14 · Known traps (do not relearn)

- **Content bleed from the reference novel** is the one error that invalidates a whole build:
  `legacy_firewall.py` is run inside `workspace_audit.py`, and `sync_styles.py` refuses to install a
  stylesheet that still carries the other book's nouns.
- Curly-vs-straight apostrophes break exact anchors — copy anchors from the file, never from memory.
- Index-arithmetic inserts into `characters.xhtml` drift by one character; use exact-anchor
  `str.replace`.
- First-`</div>` extraction grabs the label's own div — parse with ElementTree.
- Multi-edit scripts: assert every anchor before writing; discard on mid-script failure.
- A global `p{color}` beats an inherited block color — scope child rules under the block.
- `repeat_check.py` takes a **bare filename**; `audit_marks.py` needs a **real path**. Feeding either
  the wrong form produces a misleadingly clean run.
- `workspace_audit.py` needs `image-search/` and `raws/` to exist for `source_inventory.tsv`, and it
  skips the package-parity block when the deliverable has not been built (expected in setup cycles).
- `npm ci` every cycle: `node_modules` is not persisted. The sandbox can reach the npm registry and
  PyPI, but **not** jsdelivr/GStatic/GitHub raw — fonts come from `@fontsource` packages only.
- `validate_tree.py`'s CJK gate exempts `lang="ko"` runs on reference pages **and** counts them; if a
  chapter file carries the attribute, the exemption is intentionally not applied.
- ZIP timestamps change the archive hash even when payloads match, so a smoke-test hash is never a
  ship hash.
- `build_epub.py` overwrites the deliverable: never run it to "look inside".
- A wardrobe block for a person with no identity source is skipped, not faked.
- One-sided phone calls: `pc-me` only, far end as `pc-note` murmurs.
- QM false positives: wh-clefts and temporal clauses are correct periods — triage, don't blind-fix.
- Do not "fix" the reader's root `fonts.css`/`stylesheet.css`; they are references. Fork with
  `sync_styles.py`.
- Stylelint 16 has no `no-extra-semicolons` rule; a config carrying it errors out for every file.

---

## 15 · Update protocol (before every packaging)

1. Refresh the *Current at ship* header (chapters, files, manifest/spine/nav counts, image id ceiling).
2. Fold the closing cycle's new rule into its section above — merge, never append a duplicate.
   New traps → §14. New blocks/fonts → §5/§6. New gates → §9.
3. Keep this file the only place a *skill* lives; worklog §8 keeps only the *history*.
4. If a rule was learned from the previous novel's docs, restate it here in this book's terms; never
   cite its canon as the reason.

---

## 16 · Standing reader directives (this book)

1. Title **Dominating South Korea: Starting with a Golden Trait**; protagonist **Bae Do-yoon**.
2. Skill/process may be inherited from *Peninsula: Going Viral After a Dating Scandal with Kim
   Taeyeon*; **its characters and its content may not**. Nothing from that novel enters this book.
3. Structure order is Cover → Synopsis → Contents → Character Info → Introductions → Glossary →
   Chapter 1 → …
4. `fonts.css` + `stylesheet.css` define this book's fonts and styles and are preserved exactly.
5. `raws/` stores every raw; `image-search/` stores every image-search file.
6. Character imagery: web-search real photographs (search files stay in `image-search/`); cover art is
   commissioned illustration; real people keep real names, as the raw gives them.
7. Understand every step thoroughly — recon, draft, wire, gate, log, build, verify — in that order.
8. **After every final EPUB: commit and push to GitHub** on this session branch, verify the remote,
   and hand over the download link. No EPUB is built before the raws arrive.
9. **Cover.** Reuse the reader's supplied reference art as a plate, but the plate must show the
   protagonist, and it must carry the book name, the author name **DKILLER1**, and the genre in a
   colourful stylised treatment. No version strings (`Version 3`, `V1`, `Draft`) anywhere on the cover.
   Type is set live in `cover.xhtml` over a text-free plate so the lettering stays editable and crisp.
10. **Portraits.** Real people get editorial-quality photographs — a professional studio or press
    editorial, cropped to the house card ratio, never a low-res crop, never a fan snapshot. If no such
    photograph exists, AI-generate one and hold it to a 100% likeness check against the reference before
    it is approved. Source photographs stay in `image-search/`; only the finished card goes into
    `work_epub/OEBPS/images/`.
11. **Raws first.** Every supplied chapter is written to `raws/` verbatim before any drafting, wiring or
    packaging begins; the raws are then the only source a draft may be built from.
12. **Before packaging, re-scan everything**: (a) every raw beat against the §5 catalog, so no context
    that owns a style block is left in plain prose, and (b) every interrogative, so no question lost its
    `?` in translation. `style_audit.py` and `audit_marks.py` are the machine halves of that scan; the
    human half is reading the chapter against the raw a second time.
13. **This is private fiction for a single reader.** Do not sanitize, moralize, or hedge the source. Adult
    and power-fantasy material is rendered as written, tastefully and non-graphically, with no added
    editorial disapproval and no invented consent furniture.
